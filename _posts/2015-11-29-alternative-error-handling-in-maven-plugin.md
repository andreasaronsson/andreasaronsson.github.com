---
layout: post
title: "Alternative error handling in maven plugin"
description: ""
category: programming
tags: [maven,functional]
---
{% include JB/setup %}

This is a small example for anyone writing maven plugins and feels the need for
increased testability at the unit test level.

## On tools used when compiling artifacts

Artifacts can be runnable programs, documentation, libraries etc. There are many
things that fall into this category; compilers, project management, analysis
etc. These tools tend to be most conservative when it comes to compatibility
with other tools. These requirements have consequences on the behaviors they
exhibit and what patterns they follow. To emphasize productivity is is important
to manage complexity and enable reuse. The paradigm
[convention over configuration](https://en.wikipedia.org/wiki/Convention%5Fover%5Fconfiguration)
combats complexity and makes reuse easier.

## Error handling in maven plugins

Plugins extend the `AbstractMojo` and implements the `execute` method. Whenever
a plugin wants to signal a 'failed build' the contract states to throw a
`MojoFailureException`. When an unexpected problem occurs the plugin is required
to throw a `MojoExecutionException`.
[Guide to plugin development](https://maven.apache.org/guides/plugin/guide-java-plugin-development.html).

Maven as a project management tool deals to a large extent with [side
effects](https://en.wikipedia.org/wiki/Side%5Feffect%5F%27computer%5Fscience%28).
Essentially maven takes a set of instructions and then produces a side effect.
Checked exceptions are a good fit in this domain.

## Functional principles

In
[functional programming](https://en.wikipedia.org/wiki/Functional%5Fprogramming)
pure functions are a key part. They have a plethora of advantages on several
levels. One of them being testability. Say a caller wants to verify a set of
inputs. A function that always produces a return value is preferable over a
function that does not. A method that throws a checked exception may return a
value, or not. Imagine you ask someone a question that you feel is important.
Then imagine someone answering you, smiling, "Yes. Or no.". An efficient way to
annoy your co workers.

## Now for the example

It will not be possible to write pure functions here. Instead we can use a
property from the pure functions. The property to always produce a return value.
This value can be propagated or checked immediately. Unit tests will verify it
immediately. When propagated it will be used to create a checked exception. This
is what we need to communicate with the layer above us.

The usual pattern:

{% highlight java %}
void methodThatWillBeCalledByExecute() throws MojoExecutionException {
    // Do work and throw on error
}
{% endhighlight %}

With the above method an error will be propagated and the build will fail. All
good but hard to test in a unit test.

Using [Google guava](https://github.com/google/guava) or Java 8 it is possible
to use the option
[monad](https://en.wikipedia.org/wiki/Monad%5F%27functional%5Fprogramming%28) or
the [option type](https://en.wikipedia.org/wiki/Option%5Ftype). Below the
Optional from Java 8 is used:

{% highlight java %}
Optional<IOException> methodThatWillBeCalledByExecute() {
    try (file.createNewFile()) {
      // write
    } catch (IOException e) {
      return Optional.of(e);
    }
    return Optional.absent();
}
{% endhighlight %}

The above method is now a little easier to write a small test for. In the calling code, in this example the `execute` method, we can now use

{% highlight java %}
public void execute() throws MojoExecutionException {
  Optional<IOException> result = methodThatWillBeCalledByExecute();
    if (result.isPresent()) {
      throw new MojoExecutionException(result.get());
    }
}
{% endhighlight %}

Note that the use of `isPresent` is considered a [code
smell](http://mail.openjdk.java.net/pipermail/lambda-dev/2012-September/005982.html)
and in most cases `getOrElse` is prefered. Compare:

{% highlight java %}
if (!optionVar.isPresent()) {
  return DEFAULT_CONSTANT;
}
return optionVar.get();
{% endhighlight %}

with the more concise

{% highlight java %}
optionVar.getOrElse(DEFAULT_CONSTANT);
{% endhighlight %}

In the first alternative you risk making a mistake in the conditional. There are
also more lines which hurts readability.


{% include share.html %}
