---
layout: post
title: "Custom keyboard layout variant"
---

Since I normally use a swedish keyboard layout, writing braces,
parenthesis and brackets kind of sucks. I decided to remap them to

    leftbrace to AltGr+q  
    rightbrace to AltGr+r  
    leftbracket to AltGr+w  
    rightbracket to AltGr+e  
    leftparen to AltGr+a  
    rightparent to AltGr+s  


The first method I tried was to run a script in ``.kde4/Autostart`` that
runs ``xmodmap`` on a custom ``.Xmodmap`` where I captured the keypress
event with ``xev``. This was quite easy and worked as expected in just a
few minutes. However, once I logged out and the logged in again I
noticed a severe delay before I could use the keyboard. After some
thinking and googling I came to understand that the remapping of the
keys was sort of tinkering with the keymap behing the X servers back
which created a great deal of sync operations and used a lot of
resources.  The next strategy was to create the layout to be available
before the X server starts. Here is how:

``$EDITOR /usr/share/X11/xkb/symbols/se``

add the following:


    partial alphanumeric_keys
    xkb_symbols "se_aron" {
        name[Group1]="Swedish (aron)";
        include "se(basic)"
        key <AE07>  { [         7,          slash                        ]  };
        key <AE08>  { [         8                                        ]  };
        key <AE09>  { [         9                                        ]  };
        key <AE10>  { [         0,          equal                        ]  };
        key <AD01>  { [         q,          Q,      braceleft            ]  };
        key <AD02>  { [         w,          W,      bracketleft          ]  };
        key <AD03>  { [         e,          E,      bracketright         ]  };
        key <AD04>  { [         r,          R,      braceright           ]  };
        key <AC01>  { [         a,          A,      parenleft            ]  };
        key <AC02>  { [         s,          S,      parenright           ]  };
        include "kpdl(comma)"
        include "level3(ralt_switch)"
    };


Found the codes <a href="http://hack.org/mc/images/hhkb-names.png">here</a>
Now the definition exists, but it also needs to be added to a list that the systemsettings in kde can select from:

    /usr/share/X11/xkb/rules/base.lst

or with evdev

    /usr/share/X11/xkb/rules/evdev.lst

Add the entry

    se_aron         se: Swedish (aron)

And also, not quite sure this is needed but for good measure if nothing else:
Open

    /usr/share/X11/xkb/rules/base.xml

or with evdev

    /usr/share/X11/xkb/rules/evdev.xml

And, under the configitem with name 'se', add a variant like so:

    <variant>
      <configItem>
        <name>se_aron</name>
        <description>Swedish (aron)</description>
      </configItem>
    </variant>

Now, the next time you log on to a kde session (the X server needs to be restarted first) you will be able to select the custom variant. 
Update: when using fluxbox the xmodmap works just fine. .Xmodmap follows below. I also moved slash to AltGr+d:

```keycode   8 =
keycode   9 = Escape NoSymbol Escape
keycode  10 = 1 exclam exclamdown onesuperior
keycode  11 = 2 quotedbl 7 ampersand at twosuperior
keycode  12 = 3 numbersign 5 percent sterling threesuperior
keycode  13 = 4 currency 3 numbersign dollar onequarter
keycode  14 = 5 percent 1 exclam EuroSign cent
keycode  15 = 6 ampersand 9 parenleft yen fiveeighths dead_grave
keycode  16 = 7
keycode  17 = 8
keycode  18 = 9
keycode  19 = 0 equal
keycode  20 = plus question 8 asterisk backslash questiondown
keycode  21 = dead_acute dead_grave bracketright braceright plusminus notsign dead_tilde
keycode  22 = BackSpace BackSpace BackSpace BackSpace
keycode  23 = Tab ISO_Left_Tab Tab ISO_Left_Tab
keycode  24 = q Q slash question braceleft Greek_OMEGA
keycode  25 = w W comma less bracketleft Lstroke
keycode  26 = e E period greater bracketright cent dead_abovedot periodcentered
keycode  27 = r R p P braceright registered
keycode  28 = t T y Y thorn THORN
keycode  29 = y Y f F leftarrow yen
keycode  30 = u U g G downarrow uparrow
keycode  31 = i I c C rightarrow idotless
keycode  32 = o O r R oe OE
keycode  33 = p P l L thorn THORN
keycode  34 = aring Aring apostrophe quotedbl dead_diaeresis dead_abovering dead_acute dead_diaeresis
keycode  35 = asciitilde asciicircum dead_circumflex dead_circumflex
keycode  36 = Return NoSymbol Return
keycode  37 = Control_L NoSymbol Control_L
keycode  38 = a A a A parenleft
keycode  39 = s S s S parenright
keycode  40 = d D d D slash
```

The rest is default. 
