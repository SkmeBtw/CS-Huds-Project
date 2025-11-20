# CS:SOURCE OFFENSIVE - Custom Huds Using Vgui

This project shows how to install and use HUD (Heads-Up Display) mods for Counter-Strike: Source Offensive on using the source engine or similar methods.

# About / Description

This guide is for users who want to customize their CS:Source Offensive experience. Mods are applied directly through the file system. I can also help you modding in my discord channel. 

# Preview

Screenshot 1 - In progress/Absolute (Not fully completed)
![image alt](https://github.com/SkmeBtw/CS-Huds-Project/blob/0d5799071e8e411edec3a840dae578ebf8406613/snip_1000165793.jpg)

Screenshot 2 -Discontinued
![image alt](https://github.com/SkmeBtw/CS-Huds-Project/blob/0d5799071e8e411edec3a840dae578ebf8406613/Screenshot_20250730-223733_copy_1920x1080.jpg)

Screenshot 3 - In progress (The new Idea you can check the issue why) 
![image alt](https://github.com/SkmeBtw/CS-Huds-Project/blob/511cf3cadcee67aa75fc5c5fdb57edcb46db8988/images%20(2).jpeg)

They look Bad but It's still in development

# How to Install

1. Download a HUD mod.

2. Extract the contents if needed (ZIP/RAR).

3. Navigate to your game directory, usually located at:

CSSO VERSION
counter-strike source/csso/custom

4. Open or create a folder named custom inside the cstrike folder.

5. Copy and paste the HUD folder into the custom directory.

6. Launch the game. The custom HUD should now be active.


# Purpose

The goal of this project is to make HUD modding simple and accessible for users. It helps players change the in-game interface using only their Android device. (It's not easy for me) 

# Disclaimer

This is a fan-made project, not affiliated with Valve.

Always back up your files before applying mods.

Some mods may not work with every version or device.


# Contributing

If you have your own HUD mod or improvement, you’re welcome to fork the repo and submit a pull request.

# Contact

For issues or questions, open an issue on this repository.
or contact me in my official discord
Social links

DISCORD: https://discord.gg/jM7wtPDEcB

YOUTUBE: https://youtube.com/@st4nd9?si=GXODhwiduOtT6GB6

=================================================

# How to make my own Hud?

Creating Custom Panels, Buttons, & Layouts Using .res Files (Source Engine VGUI2)

This guide teaches you how to build custom UI elements in Counter-Strike: Source Offensive using VGUI2 Resource Files (.res).
No HTML. No Lua. No Derma. Pure Source Engine UI.

---

1. Folder Structure
Place your UI files inside:
cstrike/
 └── resource/
      └── ui/
          ├── MainMenu.res
          ├── ClientScheme.res
          └── ...

Any file placed here overrides the game’s original .res.

---

2. Understanding .res Files

A .res file uses KeyValues to define UI:
Panels
Buttons
Labels
Images
Colors
Fonts
Layout (xpos, ypos, wide, tall)


There is no scripting, only declarative UI layout.

---

3. Example: Custom Main Menu UI

Create:
cstrike/resource/ui/MainMenu.res
Paste the following:
"Resource/UI/MainMenu.res"
{
    "MainMenu"
    {
        "fieldName"        "MainMenu"
        "visible"          "1"
        "enabled"          "1"
        "xpos"             "0"
        "ypos"             "0"
        "wide"             "f0"
        "tall"             "f0"

        // Background Panel
        "BackgroundPanel"
        {
            "ControlName"       "Panel"
            "fieldName"         "BackgroundPanel"
            "xpos"              "0"
            "ypos"              "0"
            "wide"              "f0"
            "tall"              "f0"
            "bgcolor_override"  "20 20 20 255"
        }

        // PLAY Button
        "PlayButton"
        {
            "ControlName"       "Button"
            "fieldName"         "PlayButton"
            "xpos"              "c-100"
            "ypos"              "200"
            "wide"              "200"
            "tall"              "40"

            "labelText"         "PLAY"
            "font"              "MenuLarge"
            "fgcolor"           "255 255 255 255"
            "bgcolor_override"  "50 120 255 255"

            "command"           "engine playdemo menu_startup"
        }

        // SETTINGS Button
        "SettingsButton"
        {
            "ControlName"       "Button"
            "fieldName"         "SettingsButton"
            "xpos"              "c-100"
            "ypos"              "250"
            "wide"              "200"
            "tall"              "40"

            "labelText"         "SETTINGS"
            "font"              "MenuLarge"
            "fgcolor"           "255 255 255 255"
            "bgcolor_override"  "60 60 60 255"

            "command"           "optionsdialog"
        }

        // QUIT Button
        "QuitButton"
        {
            "ControlName"       "Button"
            "fieldName"         "QuitButton"
            "xpos"              "c-100"
            "ypos"              "300"
            "wide"              "200"
            "tall"              "40"

            "labelText"         "QUIT"
            "font"              "MenuLarge"
            "fgcolor"           "255 255 255 255"
            "bgcolor_override"  "180 30 30 255"

            "command"           "quit"
        }
    }
}

This creates:

A full-screen dark background

A centered PLAY button

Settings and Quit buttons

Styled entirely via .res

---

4. Adding a Custom Logo

Add this inside MainMenu.res:

"GameLogo"
{
    "ControlName" "ImagePanel"
    "fieldName"   "GameLogo"
    "xpos"        "c-128"
    "ypos"        "50"
    "wide"        "256"
    "tall"        "128"
    "image"       "vgui/cssologo"
    "scaleImage"  "1"
}

Place your materials:

cstrike/materials/vgui/cssologo.vtf
cstrike/materials/vgui/cssologo.vmt

Minimal .vmt:

"UnlitGeneric"
{
    "$basetexture" "vgui/cssologo"
    "$translucent" "1"
}

---

5. Creating Custom Panels

You can customize UI modules by defining your own reusable panels.

Example:

"SidePanel"
{
    "ControlName" "Panel"
    "fieldName"   "SidePanel"
    "xpos"        "0"
    "ypos"        "0"
    "wide"        "300"
    "tall"        "f0"
    "bgcolor_override" "30 30 30 255"

    "SideLabel"
    {
        "ControlName" "Label"
        "fieldName"   "SideLabel"
        "xpos"        "10"
        "ypos"        "10"
        "wide"        "280"
        "tall"        "30"
        "labelText"   "CSSO PANEL"
        "font"        "MenuLarge"
        "fgcolor"     "255 255 255 255"
    }
}

You can insert this panel anywhere in MainMenu or other UI files.

---

6. Useful Positioning Values

VGUI2 supports special keywords:

Value	Meaning
100	Absolute pixels
c-50	Centered minus 50px
c0	Centered exactly
f0	Fill parent (full width/height)
cs-0.5	Center scaled

Example of centering a panel:

"xpos" "c-150"
"ypos" "c-50"

---

⚠ 7. Limitations of .res

.res cannot:
run scripts
animate
detect mouse hover
change colors dynamically
move UI dynamically
display HTML
They are static UI layouts only.

---

8. Recommended Files to Edit in CSSO

You can modify any of these:

MainMenu.res
OptionsDialog.res
ScoreBoard.res
Loading.res
HudLayout.res
HudPlayerHealth.res
HudWeaponSelection.res
TeamMenu.res
BuyMenu.res
ClientScheme.res

---

9. Tips for Clean UI

Use ClientScheme.res to define custom fonts & colors
Keep spacing consistent (20–40px padding)
Use bgcolor_override for fast coloring
Test UI changes by restarting the game or using reloadscheme

---

10. Ready-Made Example Repository Structure
CSSO-VGUI2-Tutorial/
 ├── csso
 └── ui/
      ├── MainMenu.res
      ├── ClientScheme.res
      └── example_logo/
            ├── cssologo.vtf
            └── cssologo.vmt

================================================

# How to make Fonts(textslabels)/Panels

have different colors?
1. Main Menu File (ClientScheme/VGUI)
CSSO uses the same menu file as CS:S:
resource/GameMenu.res
To add your own panel area and text, you edit or create:
resource/UI/MainMenu.res

---

2. Add a Panel + Label (VGUI .res format)
resource/UI/MainMenu.res

"MainMenu"
{
    "MyCustomPanel"
    {
        "ControlName"   "Panel"
        "fieldName"     "MyCustomPanel"
        "xpos"          "c-200"
        "ypos"          "c-100"
        "wide"          "400"
        "tall"          "200"
        "visible"       "1"
        "enabled"       "1"
        "paintbackground" "1"
        "bgcolor_override" "0 0 0 150"
    }
}

    "MyCustomLabel"
    {
        "ControlName"   "Label"
        "fieldName"     "MyCustomLabel"
        "xpos"          "c-180"
        "ypos"          "c-80"
        "wide"          "360"
        "tall"          "40"
        "visible"       "1"
        "enabled"       "1"
        "labelText"     "Hello from CSSO"
        "textAlignment" "center"
        "fgcolor_override" "255 255 255 255"
        "font"          "Trebuchet24"
    }
}

The Colorable Sets:
"paintbackground" "0/1"
"bgcolor_override" "0 0 0 0" = Panels,vtf.
"fgcolor_override" "0 0 0 0" = Texts, Messages. 
Format: #RRGGBB or #RRGGBBAA (Red, Green, Blue, Alpha).

This creates:
A centered panel with a transparent dark background
A centered label with white text inside it

---

3. File Placement

Make sure these files exist in CSSO’s directory structure:
css_offensive/custom/<your_mod_name>/resource/UI/MainMenu.res
css_offensive/custom/<your_mod_name>/resource/ClientScheme.res
css_offensive/custom/<your_mod_name>/resource/sourcescheme.res
If you don’t use a custom folder, put it directly:
css_offensive/resource/UI/MainMenu.res
Restart the game after changes.

=================================================


