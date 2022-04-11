---
layout: page
title: User Guide
---
UNite is a **desktop app for managing contacts specifically designed for people in University**. It is optimized for use via a Command Line Interface (CLI) while still having the benefits of a Graphical User Interface (GUI). If you want an easy-to-use app to manage your University contacts, UNIte is the right place to go!


* **Table of Contents**
{:toc}


--------------------------------------------------------------------------------------------------------------------
<div style="page-break-after: always;"></div>

## Quick start<a name="quick-start"></a>

1. Ensure you have Java `11` or above installed in your Computer.

1. Download the latest `UNite.jar` from [here](https://github.com/AY2122S2-CS2103T-W12-2/tp/releases).

1. Copy the file to the folder you want to use as the _home folder_ for your UNite.

1. Double-click the file to start the app. The GUI similar to the below should appear in a few seconds. Note how the app contains some sample data.<br>
   ![Main](images/Main.png)

Refer to the [Features (CLI)](#features-cli) below for details of each command.

Some features are able to be operated via mouse interactions, most of these are disabled by default while some are not, refer to [Features (Mouse interaction)](#features-mouse-interaction) below for more details.


<div style="page-break-after: always;"></div>

## Features (CLI)<a name="features-cli"></a>

Below are the features that can be completed using command line interface (CLI).

<div markdown="block" class="alert alert-info">

**Notes about the command format:**<br>

* Words in `UPPER_CASE` are the parameters to be supplied by the user.<br>
  e.g. in `add n/NAME`, `NAME` is a parameter which can be used as `add n/John Doe`.

* Items in square brackets are optional.<br>
  e.g `n/NAME [t/TAG]` can be used as `n/John Doe t/friend` or as `n/John Doe`.

* Items with `…`​ after them can be used multiple times including zero times.<br>
  e.g. `[t/TAG]…​` can be used as ` ` (i.e. 0 times), `t/friend`, `t/friend t/family` etc.

* Parameters can be in any order.<br>
  e.g. if the command specifies `n/NAME p/PHONE_NUMBER`, `p/PHONE_NUMBER n/NAME` is also acceptable.

* If a parameter is expected only once in the command but you specified it multiple times, only the last occurrence of the parameter will be taken.<br>
  e.g. if you specify `p/12341234 p/56785678`, only `p/56785678` will be taken.

* Extraneous parameters for commands that do not take in parameters (such as `help`, `list`, `exit`, `clear` and `clear_emptytag`) will be ignored.<br>
  e.g. if the command specifies `help 123`, it will be interpreted as `help`.

</div>

<div style="page-break-after: always;"></div>

### Add a new person: `add`<a name="add-a-new-person"></a>

Add a new person to UNite.

Format: `add n/NAME p/PHONE e/EMAIL a/ADDRESS [c/COURSE] [tele/TELEGRAM] [m/MATRICCARD] [t/TAG]`

* The order of input does not matter.
* `n/NAME p/PHONE e/EMAIL a/ADDRESS` are the 4 required information that must be present.
* Can attach multiple tags to the person at the same time, each tag must follow the format `t/TAG`
* Two `Person` are considered the same `Person` if 
  * They have the same `Name` (case-insensitive).
  * At least one of following fields: `Email`, `Phone`, `Address`, `MatricCard`) is the same (case-insensitive) between these two `Person`.

Examples:
* `add n/Peter p/12345678 e/peter@gmail.com a/1 Computing Drive t/classmates t/friends
c/computer science tele/peterrocks m/A0123456X` <br>
This command will add a new person whose name is `Peter`, with phone number
`12345678`, email address `peter@gmail.com` and telegram `peterrocks`. Peter's address is `1 Computing Drive`, he is
taking `computer science` as his course, his matriculation card number is `A0123456X`. The user categorize
Peter with tags `classmates` and `friends`.
* `add n/Aaron p/2345678 e/aaron@gmail.com` <br>
This command will not get executed successfully, because of the missing required field `a/ADDRESS`.

<div markdown="block" class="alert alert-info">

**Notes about Input Validation Rules**<a name="input-validation"></a>

There are certain rules that users should follow for input to be considered valid (applies to all commands). Please refer to the following.

 * **NAME**<br>
    NAME is case-insensitive and it should only contain alphanumeric characters and spaces (maximum 50 characters including spaces), and it should not be blank.
     * Valid Examples - `Alice Tan`, `Alice3tan`
     * Invalid Examples - `peter*`


 * **EMAIL** <br> 
    Emails should be of the format `local-part@domain` and adhere to the following constraints:
     1. The local-part should only contain alphanumeric characters and these special characters, excluding the parentheses, (+_.-). The local-part may not start or end with any special characters, and two or more special characters cannot appear consecutively.
     2. This is followed by a '@' and then a domain name. The domain name is made up of domain labels separated by compulsory periods. The domain name must:
         * end with a domain label at least 2 characters long
         * have each domain label start and end with alphanumeric characters
         * have each domain label consist of alphanumeric characters, separated only by hyphens, if any
    * Valid Examples - `aliceTan@gmail.com`, `123@co.cn` 
    * Invalid Examples - `peterjack@@example.com`, `peterjack@-`, `peterjack@gmail`


 * **PHONE**<br>
    Phone numbers should only contain numbers, and it should be at least 3 digits long
     * Valid Examples - `12341234`, `123`
     * Invalid Examples - `@123123`, `dasd123 123`


 * **ADDRESS**<br>
    Addresses can take any values (including non-english characters), and it should not be blank
     * Valid Examples - `Blk 456, Den Road, #01-355`, `-`
     * Invalid Examples - ``


 * **TELEGRAM**<br> 
     Telegram ID should only contain alphanumeric characters and underscore. It should be one word and must not start with an underscore.
      * Valid Examples - `alice_test_1234`, `alice123`
      * Invalid Examples - `_alice`, `@alice`


 * **COURSE**<br>
     Course should only contain alphabet characters and spaces.
      * Valid Examples - `Computer Science and Mathematics`, `Math`
      * Invalid Examples - `123`, `Computer_Science`


 * **MATRIC CARD**<br>
     Matric Card should only contain alphanumeric characters, and it should be one word
      * Valid Examples - `A1231234E`
      * Invalid Examples - `alice test`, `@A1231234E`


 * **TAG**<br>
     Tag should only contain alphanumeric characters, and it should be one word
      * Valid Examples - `CS2100`
      * Invalid Examples - `CS_2100`, `C S 2 1 0 0`

</div>

<div style="page-break-after: always;"></div>

### Edit a person : `edit`<a name="edit-a-person"></a>

Edit a person in the UNite.

Format: `edit INDEX [n/NAME] [p/PHONE] [e/EMAIL] [a/ADDRESS] [t/TAG]…​ [c/COURSE] [m/MATRICCARD] [tele/TELEGRAM]`

* Edit the person at the specified `INDEX`. The index refers to the index number shown in the displayed person list. The index **must be a positive integer** 1, 2, 3, …​
* At least one of the optional fields must be provided.
* Existing values will be updated to the input values.
* When editing tags, the existing tags of the person will be removed i.e adding of tags is not cumulative.
* When editing tags, duplicate tags are considering as one tag.
* You can remove all the person’s tags by typing `t/` without
  specifying any tags after it.

Examples:
* `edit 1 p/91234567 e/johndoe@example.com` <br> Edits the phone number and email address of the 1st person to be `91234567` and `johndoe@example.com` respectively.
* `edit 2 n/Betsy Crower t/` <br> Edits the name of the 2nd person to be `Betsy Crower` and clears all existing tags.
* `edit 2 n/Betsy Crower t/tag1 t/tag1 t/tag1` <br> Edits the name of the 2nd person to be `Betsy Crower` and creates only one tag `tag1`.

<div style="page-break-after: always;"></div>

### Add a new tag : `add_tag`<a name="add-a-new-tag"></a>

Add a new tag to UNite.

Format: `add_tag t/TAG_NAME`

Examples:
* `add_tag t/Students`<br> Adds a new tag called "Students" if it does not yet exist.
* `add_tag t/Professors`<br> Adds a new tag called "Professors" if it does not yet exist.

### Delete a tag : `delete_tag`<a name="delete-a-tag"></a>

Delete an existing tag from UNite.

Format: `delete_tag INDEX`

* Deletes the tag at the specified `INDEX`. 
* The index refers to the index number shown in the displayed tag list.
* The index **must be a positive integer** 1, 2, 3, …​

Examples:
* `delete_tag 1`<br> Deletes the tag at index number 1 if there is any.
* `delete_tag 10`<br> Deletes the tag at index number 10 if there is any.

<div style="page-break-after: always;"></div>

### List all tags : `list_tag`<a name="list-all-tags"></a>

List out all tags current exist in UNite.

<p align="center">
    <img src="images/list_tag.png" width="500"/>
</p>

Format: `list_tag`
<div style="page-break-after: always;"></div>

### Attach tag to a profile: `attach`<a name="attach-tag-to-a-profile"></a>

Add an existing tag to a profile.

Format: `attach t/TAG_NAME i/PROFILE_INDEX`

* Attach the tag of `TAG_NAME` to the person at the specified `PROFILE_INDEX`.
* The index refers to the index number shown in the displayed person list.
* The index **must be a positive integer** 1, 2, 3, …​

Examples:
* `attach t/Students i/1`<br> Attaches the tag "Students" to the person at index 1, if both the tag and the person exist.
* `attach t/Professors i/10`<br> Attaches the tag "Professors" to the person at index 10, if both the tag and the person exist.

### Detach a tag from a profile : `detach`<a name="detach-a-tag-from-a-profile"></a>

Remove the tag from a profile’s tags.

Format: `detach t/TAG_NAME i/PROFILE_INDEX`

* Remove the tag of `TAG_NAME` from the person at the specified `PROFILE_INDEX`.
* The index refers to the index number shown in the displayed person list.
* The index **must be a positive integer** 1, 2, 3, …​

Examples:
* `detach t/Students i/1`<br> Detaches the tag "Students" from the person at index 1, if the person exists and the person has a tag called "Students".
* `detach t/Professors i/10`<br> Detaches the tag "Professors" from the person at index 10, if the person exists and the person has a tag called "Professors".

<div style="page-break-after: always;"></div>

### Filter list by tag: `filter`<a name="filter-list-by-tag"></a>
Filters the full contact list with an existing tag. List will not get updated if tag does not exist. To clear the
filter, simply input the `list` command.

Format: `filter TAG_NAME`

### Add remark to a tag: `remark_tag`
Modifies the remark of an existing tag. The existing remark will be replaced by the new remark entered. 

Format: `remark_tag t/TAG_NAME r/REMARK` 

Examples: 
* `remark_tag t/labGroup1 r/report due 1st May` changes the remark for tag `labGroup1` to 'report due 1st May'.
* `remark_tag t/labGroup1 r/` clears the remark for tag `labGroup1`.

### Remove all empty tags: `clear_emptytag`
Removes all tags that are not attached to any person.

Format: `clear_emptytag`

### Locate person by name: `find`<a name="locate-person-by-name"></a>

Finds persons whose names contain the keyword exactly.

Format: `find KEYWORD [MORE_KEYWORDS]`

* The search is case-insensitive. e.g `hans` will match `Hans`
* The order of the keywords does not matter. e.g. `Hans Bo` will match `Bo Hans`
* Only the name is searched.
* Only full words will be matched e.g. `Han` will not match `Hans`
* Persons matching at least one keyword will be returned (i.e. `OR` search).
  e.g. `Hans Bo` will return `Hans Gruber`, `Bo Yang`

Examples:
* `find John` returns `john` and `John Doe`
* `find alex david` returns `Alex Yeoh`, `David Li`<br>

<p align="center">
    <img src="images/find_yu_li.png" width="500"/>
</p>


<div style="page-break-after: always;"></div>

### Grab person's attribute : `grab`<a name="grab-person-attribute"></a>

Grabs person's (single or multiple) attribute and display out, allow the user to copy directly.

Format: `grab ATTRIBUTE_PREFIX/[INDEX] [t/TAG]`

* `INDEX` is optional. If an index is provided, it will grab the attribute of the person with this `INDEX`. If it
is left blank, it will grab this attribute of all the persons in UNite.
* The available `ATTRIBUTE_PREFIX` that you can grab are `n/` for name, `p/` for phone number, `e/` for email,
`a/` for address, `c/` for course, `m/` for matric card, `tele/` for telegram.
* `TAG` are optional too. If no tags are provided, it will by default grab the attribute of the person
  with the `INDEX` or grab from all person if `INDEX` was not present.
* When `TAG` is provided, you cannot have `INDEX` present. You will grab the 
attributes from all person with the `TAG`. You can only provide 1 tag.

Examples:
* `grab e/1` <br> Grabs the email address of person with index 1.
* `grab tele/` <br> Grabs the telegram id of everyone inside UNite.
* `grab tele/ t/friends` <br> Grabs the telegram id of everyone tagged as "friends" inside UNite.

<p align="center">
    <img src="images/grab-email.png" width="500"/>
</p>


<div style="page-break-after: always;"></div>

### Delete a person : `delete`<a name="delete-a-person"></a>

Deletes the specified person from the UNite.

Format: `delete INDEX`

* Deletes the person at the specified `INDEX`.
* The index refers to the index number shown in the displayed person list.
* The index **must be a positive integer** 1, 2, 3, …​

Examples:
* `list` followed by `delete 2` deletes the 2nd person in UNite.
* `filter friends` followed by `delete 1` deletes the 1st person in the filtered list generated by the `filter`command.
* `find Betsy` followed by `delete 1` deletes the 1st person in the results of the `find` command.

<div style="page-break-after: always;"></div>

### Change the theme: `theme`<a name="change-the-theme"></a>
Change the appearance of UNite to the specified theme, either `dark` or `light`.

Format: `theme THEME`
* `THEME` can only be either `dark` or `light`, nothing else.

Examples:
* `theme dark` changes UNite to dark theme, which is also the default theme.

<p align="center"> 
    <img src="images/dark_theme.png" width="500"/>
</p>

<div style="page-break-after: always;"></div>

* `theme light` changes UNite to light theme.

<p align="center"> 
    <img src="images/light_theme.png" width="500"/>
</p>

<div style="page-break-after: always;"></div>

### View detailed profile: `profile`<a name="view-detailed-profile-cli"></a>
View detailed information about the specified person in the form of profile, displayed at
the right-hand side of the screen.

Format: `profile INDEX`

* View the profile of a person at the specified `INDEX`.
* The index refers to the index number shown in the displayed person list.
* The index **must be a positive integer** 1, 2, 3, …​

Examples:
* `list` followed by `profile 2` displays the 2nd person's profile at the right-hand side.
<p align="center">
    <img src="images/profile.png" width="400"/>
</p>

* `filter friends` followed by `profile 3` displays the 3rd person's profile in the filtered list generated
by the `filter`command.
* `find Betsy` followed by `profile 1` displays the 1st person's profile in the results of the `find` command.

### Clear all entries : `clear`<a name="clear-all-entries"></a>

Clears all entries from UNite. 
* If extra spaces or characters are entered before or after the `clear` keyword, an error message will popup. This is
to prevent users from accidentally emptying UNite.

Format: `clear`

### Exit the program : `exit`<a name="exit-the-program"></a>

Exits the program.

Format: `exit`

### Save the data<a name="save-the-data"></a>

All data in UNIte are saved in the hard disk automatically after any command that changes the data. There is no need to save manually.

### Edit the data file<a name="edit-the-data-file"></a>

Data in UNite are saved as a JSON file `[JAR file location]/data/unite.json`. Advanced users are welcome to update data directly by editing that data file.

<div markdown="span" class="alert alert-warning">:exclamation: **Caution:**
If your changes to the data file makes its format invalid, UNite will discard all data and start with an empty data file at the next run.
</div>

--------------------------------------------------------------------------------------------------------------------
<div style="page-break-after: always;"></div>

## Features (Mouse interaction)<a name="features-mouse-interaction"></a>

By default, features that allow mouse interactions are disabled in UNite unless otherwise stated. However, users who are not familiar with using CLI can enable
it. Below are the features that are supported by mouse interactions.

**Note:** Some features included in the [Features (CLI)](#features-cli) section cannot be done using mouse interaction. To execute those features,
enter the command in the command box and follow the instructions in the previous section.

Shown below are the annotated screenshots of UNite for reference to UI components:

<p align="center">
    <img src="images/UNite_annotated.png" width="400"/>  <img src="images/UNite_profile.png" width="400"/> <br>
<img src="images/UNite_taglist.png" width="400"/>  <img src="images/UNite_grabresult.png" width="400"/>
</p>

<div style="page-break-after: always;"></div>

### Enable mouse interaction : `enable_mouseUX`<a name="enable-mouse-interaction"></a>
Enables mouse interaction in mouseUX. After enabling mouse interactions, 3 new buttons ("Add", "Tags" and "Theme") will
appear on the menu bar as shown in the figure below.

<p align="center">
    <img src="images/enableMouseUX_menuBar.png" width="250"/>
</p>

Right-click operation is also enabled for both person list panel and tag list.

Format: `enable_mouseUX`

### Disable mouse interaction : `disable_mouseUX`<a name="disable-mouse-interaction"></a>
Disables mouse interaction in mouseUX. After disabling, buttons in menu bar that help users access pop up windows will disappear, right-click operation for both person list panel and tag list are disabled.
The 2 mouse interactions below are still maintained (these 2 features are enabled by default and cannot be disabled):
* View a profile by left-clicking on a person in person list panel.
* Filter contact list by left-clicking on the tag list.

Format: `disable_mouseUX`

### View detailed profile<a name="view-profile-click"></a>
To view a profile, left-click on the person in the person list panel. As mentioned, this feature is enabled by default and cannot be disabled.

<div style="page-break-after: always;"></div>

### Add a new profile<a name="add-a-new-person-click"></a>

To add a new profile, click the `Add` button in menu bar, and select `Add Profile`. An **Add Profile pop-up
window** will appear.

<p align="center">
    <img src="images/addProfileNew_popup.png" width="250"/>
</p>

In the window, simply enter all related information into the spaces provided, and click the
`Save` button to add a new profile. Click `Cancel` to stop adding and close the pop-up window.

<div style="page-break-after: always;"></div>

### Delete person<a name="delete-person"></a>

To delete a person, right-click on the profile and select `Delete`.

<p align="center">
    <img src="images/deleteProfile_GUI.png" width="250"/>
</p>


### Add a new tag<a name="add-a-new-tag-click"></a>

To add a new tag, click the `Tags` button on the menu bar, and select `Tags`. A **Tags pop-up window** will appear.

<img src="images/tag_popup.png" width="300"/>


Enter the new tag name into the text field, and click the `Add` button to create a new tag. To cancel adding tags, click
the `Cancel` button to close the pop-up window.

### Delete tag<a name="delete-tag-click"></a>
To delete a tag, open the tag pop-up window as explained in [Add a new tag](#add-a-new-tag-click). Click the `Select` button to enable
selection. Select the tag(s) to delete, and click the `Delete` button to delete all the selected tags.

Selected tags will appear in white, as shown in the figure below ("friends", "classmates" and "Professors" selected).

<p align="center">
    <img src="images/selectedTag_GUI.png" width="250"/>
</p>

Another approach to delete a tag one at a time is to right-click on a tag in tag list, and click on `Delete Tag` as shown below.

<p align="center">
    <img src="images/selectedTag_taglist.png" width="250"/>
</p>

<div style="page-break-after: always;"></div>

### Filter list by tag<a name="filter-list-by-tag-click"></a>
To filter the list of person by tag directly, first display all the tags by input the command `list_tag`, then simply left-click on the tag to filter the list. As mentioned, this feature is enabled by default and cannot be disabled.

<p align="center">
    <img src="images/filter-through-click.png" width="300"/>
</p>

--------------------------------------------------------------------------------------------------------------------
<div style="page-break-after: always;"></div>

## FAQ<a name="faq"></a>

**Q**: How do I transfer my data to another Computer?<br>
**A**: Install the app in the other computer and overwrite the empty data file it creates with the file that contains the data of your previous UNite home folder.<br>
**Q**: How do I clear the "tag filter" after I typed the `filter` command?<br>
**A**: Use `list` command to clear the filter.<br>
**Q**: How do I clear the general display if I just want it to be empty?<br>
**A**: Unfortunately, this is not the intentioned and cannot be done explicitly. The only times general display can be empty are when you first launch the app and use commands that do not change the general display, and when you delete a person who is currently being displayed as profile.

  --------------------------------------------------------------------------------------------------------------------
<div style="page-break-after: always;"></div>

## Command summary<a name="command-summary"></a>

Action | Command format, Examples                                                                                                                                          | Mouse Interaction
--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------
**add** | `add n/NAME p/PHONE_NUMBER e/EMAIL a/ADDRESS [t/TAG]…​`<br> e.g., `add n/James Ho p/22224444 e/jamesho@example.com a/123, Clementi Rd, 1234665 t/friend t/colleague` | (Menu bar) `Add ` -> `Add Profile`
**add_tag**| `add_tag t/TAG_NAME`                                                                                                                                              | (Menu bar) `Tags` -> `Tags`, enter tag name in text field -> select `Add`
**attach** | `attach t/TAGNAME i/PERSON_INDEX`                                                                                                                             | -
**clear** | `clear`  <br/>                                                                                                                                                    | -
**clear_emptytag** | `clear_emptytag`                                                                                                                                                  | -
**delete** | `delete INDEX`<br> e.g., `delete 3`                                                                                                                               | (Person list panel) right-click on a person -> select `Delete`
**delete_tag**| `delete TAG_INDEX`<br> e.g., `delete_tag 3`                                                                                                                       | (Menu bar) `Tags` -> `Tags`, enable `Select` -> select tags and choose `Delete` <br> Or, (Command box) type command `list_tag` -> (Tag list) right-click on a tag -> select `Delete Tag`
**detach** | `detach t/TAGNAME i/PERSON_INDEX`                                                                                                                             | -
**disable_mouseUX** | `disable_mouseUX`                                                                                                                                                 | -
**edit** | `edit INDEX [n/NAME] [p/PHONE] [e/EMAIL] [a/ADDRESS] [t/TAG]…​ [c/COURSE] [m/MATRICCARD] [tele/TELEGRAM]`<br> e.g.,`edit 2 n/James Lee e/jameslee@example.com`                                               | -
**enable_mouseUX** | `enable_mouseUX`                                                                                                                                                  | -
**exit** | `exit`                                                                                                                                                            | -
**filter** | `filter TAGMAME`                                                                                                                                                | (Command box) type command `list_tag` -> (Tag list) left-click on a tag
**find** | `find KEYWORD [MORE_KEYWORDS]`<br> e.g., `find James Jake`                                                                                                                     | -
**grab** | `grab ATTRIBUTE_PREFIX/[INDEX] [t/TAGS]`<br> e.g., `grab e/ t/classmates`                                                                                         | -
**help** | `help`                                                                                                                                                            | (Menu bar) `Help` -> `Help`
**list** | `list`                                                                                                                                                            | -
**list_tag** | `list_tag`                                                                                                                                                        | (Menu bar) `Tags` -> `Tags`. All tags are displayed in the "Current tags" section.
**profile** | `profile INDEX`<br> e.g., `profile 3`                                                                                                                             | (Person list panel) left-click on a person
**remark_tag** | `remark_tag t/TAG_NAME r/REMARK`<br> e.g., `remark t/classmates r/My classmates for CS2103T` | -
**theme** | `theme THEME`<br> e.g., `theme light`                                                                                                                             | -

