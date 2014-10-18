---
layout: post
title: "Custom keyboard layout variant"
---

Since I normally use a swedish keyboard layout, writing braces, parenthesis and brackets kind of sucks. I decided to remap them to

    leftbrace to AltGr+q  
    rightbrace to AltGr+r  
    leftbracket to AltGr+w  
    rightbracket to AltGr+e  
    leftparen to AltGr+a  
    rightparent to AltGr+s  


The first method I tried was to run a script in ".kde4/Autostart" that runs "xmodmap" on a custom ".Xmodmap" where I captured the keypress event with "xev". This was quite easy and worked as expected in just a few minutes. However, once I logged out and the logged in again I noticed a severe delay before I could use the keyboard. After some thinking and googling I came to understand that the remapping of the keys was sort of tinkering with the keymap behing the X servers back which created a great deal of sync operations and used a lot of resources. 
The next strategy was to create the layout to be available before the X server starts. Here is how:

``edit /usr/share/X11/xkb/symbols/se``

add the following:

<pre>
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
</pre>
Found the codes <a href="http://hack.org/mc/images/hhkb-names.png">here</a>
Now the definition exists, but it also needs to be added to a list that the systemsettings in kde can select from:

    /usr/share/X11/xkb/rules/base.lst

or with evdev

    /usr/share/X11/xkb/rules/evdev.lst

Add the entry

``se_aron         se: Swedish (aron)``

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
<pre>
keycode   8 =
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
keycode  41 = f F u U dstroke ordfeminine
keycode  42 = g G i I eng ENG
keycode  43 = h H d D hstroke Hstroke
keycode  44 = j J h H dead_hook dead_horn
keycode  45 = k K t T kra ampersand
keycode  46 = l L n N lstroke Lstroke
keycode  47 = odiaeresis Odiaeresis s S oslash Oslash
keycode  48 = adiaeresis Adiaeresis minus underscore ae AE
keycode  49 = section onehalf grave
keycode  50 = Shift_L NoSymbol Shift_L
keycode  51 = apostrophe asterisk backslash bar acute multiply
keycode  52 = z Z semicolon colon guillemotleft less dead_ogonek dead_doubleacute
keycode  53 = x X q Q guillemotright greater
keycode  54 = c C j J copyright copyright
keycode  55 = v V k K leftdoublequotemark leftsinglequotemark
keycode  56 = b B x X rightdoublequotemark rightsinglequotemark
keycode  57 = n N b B n N
keycode  58 = m M m M mu masculine
keycode  59 = comma semicolon w W dead_cedilla dead_ogonek
keycode  60 = period colon v V periodcentered dead_abovedot
keycode  61 = minus underscore z Z dead_belowdot dead_abovedot
keycode  62 = Shift_R NoSymbol Shift_R
keycode  63 = KP_Multiply KP_Multiply KP_Multiply KP_Multiply KP_Multiply KP_Multiply XF86ClearGrab KP_Multiply KP_Multiply XF86ClearGrab
keycode  64 = Alt_L Meta_L Alt_L Meta_L
keycode  65 = space space space space space nobreakspace space nobreakspace
keycode  66 = Caps_Lock NoSymbol Caps_Lock
keycode  67 = F1 F1 F1 F1 F1 F1 XF86Switch_VT_1 F1 F1 XF86Switch_VT_1
keycode  68 = F2 F2 F2 F2 F2 F2 XF86Switch_VT_2 F2 F2 XF86Switch_VT_2
keycode  69 = F3 F3 F3 F3 F3 F3 XF86Switch_VT_3 F3 F3 XF86Switch_VT_3
keycode  70 = F4 F4 F4 F4 F4 F4 XF86Switch_VT_4 F4 F4 XF86Switch_VT_4
keycode  71 = F5 F5 F5 F5 F5 F5 XF86Switch_VT_5 F5 F5 XF86Switch_VT_5
keycode  72 = F6 F6 F6 F6 F6 F6 XF86Switch_VT_6 F6 F6 XF86Switch_VT_6
keycode  73 = F7 F7 F7 F7 F7 F7 XF86Switch_VT_7 F7 F7 XF86Switch_VT_7
keycode  74 = F8 F8 F8 F8 F8 F8 XF86Switch_VT_8 F8 F8 XF86Switch_VT_8
keycode  75 = F9 F9 F9 F9 F9 F9 XF86Switch_VT_9 F9 F9 XF86Switch_VT_9
keycode  76 = F10 F10 F10 F10 F10 F10 XF86Switch_VT_10 F10 F10 XF86Switch_VT_10
keycode  77 = Num_Lock NoSymbol Num_Lock
keycode  78 = Scroll_Lock NoSymbol Scroll_Lock
keycode  79 = KP_Home KP_7 KP_Home KP_7
keycode  80 = KP_Up KP_8 KP_Up KP_8
keycode  81 = KP_Prior KP_9 KP_Prior KP_9
keycode  82 = KP_Subtract KP_Subtract KP_Subtract KP_Subtract KP_Subtract KP_Subtract XF86Prev_VMode KP_Subtract KP_Subtract XF86Prev_VMode
keycode  83 = KP_Left KP_4 KP_Left KP_4
keycode  84 = KP_Begin KP_5 KP_Begin KP_5
keycode  85 = KP_Right KP_6 KP_Right KP_6
keycode  86 = KP_Add KP_Add KP_Add KP_Add KP_Add KP_Add XF86Next_VMode KP_Add KP_Add XF86Next_VMode
keycode  87 = KP_End KP_1 KP_End KP_1
keycode  88 = KP_Down KP_2 KP_Down KP_2
keycode  89 = KP_Next KP_3 KP_Next KP_3
keycode  90 = KP_Insert KP_0 KP_Insert KP_0
keycode  91 = KP_Delete KP_Separator KP_Delete KP_Separator
keycode  92 = ISO_Level3_Shift NoSymbol ISO_Level3_Shift
</pre>
The rest is default. 
