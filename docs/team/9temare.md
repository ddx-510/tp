---
layout: page
title: Wang Zihao's Project Portfolio Page
---

## Project: UNite

UNite is a **desktop application meant for managing contacts for people in university, it works best for school administrators and teaching assistants**. UNite is tailored for blazing operation speed via Command Line Interface (CLI), while keeping the benefits and convenience of an intuitive Graphical Interface (GUI) with mouse-optimized user experience (MouseUX). 
UNite is built in Java with JavaFX powering the GUI, it has about 10 kLoC.

This is Wang Zihao, one of the developers behind UNite. My focus in the project is mainly targeted at optimizing GUI. I am dedicated to present users their operation results satisfyingly, with the user experience of "What you think is what you get".

Given below are my contributions to the project.

### New Features
  * **New Feature 1**: Switch Theme Command ([#45](https://github.com/AY2122S2-CS2103T-W12-2/tp/pull/45) [#72](https://github.com/AY2122S2-CS2103T-W12-2/tp/pull/72))
    * **What it does:** Allow user to change the appearance of UNite, by switching between dark and light theme. The default theme is dark theme.
    * **Justifications:** This feature allows user to work with UNite comfortably both in dark and bright environment. It also allows user to style up their UNite, to make UNite more personalized.
    * **Highlights:** This feature can be invoked via CLI with easy to remember command, and via MouseUX with clear navigation once MouseUX is enabled.


  * **New Feature 2**: Profile Command ([#52](https://github.com/AY2122S2-CS2103T-W12-2/tp/pull/52) [#83](https://github.com/AY2122S2-CS2103T-W12-2/tp/pull/83))
    * **What it does:** Allow user view detailed information of a person that is not displayed in the person cards on the left-hand side on UNite.
    * **Justifications:** With people being displayed in a list on the left-hand side of UNite, user can only glance limited information in a concise manner. But the Profile feature enables user to view detailed information about a person, including telegram handle and course information, in bigger section on the right-hand side of UNite.
    * **Highlights:** This feature can be invoked via CLI, but it works most intuitively with MouseUX (MouseUX does not need to be enabled for this feature). The user can simply click on a person of interest, and the detailed information is displayed immediately on the right-hand side of UNite.


  * **New Feature 3**: Delete person via MouseUX ([#55](https://github.com/AY2122S2-CS2103T-W12-2/tp/pull/55) [#184](https://github.com/AY2122S2-CS2103T-W12-2/tp/pull/184))
    * **What it does:** Allow user to right-click on a person in the list on the left-hand side on UNite to perform Delete Command.
    * **Justifications:** With CLI only, it is sometimes troublesome to delete a person of interest, deleting a person by accident is also possible if the index specified by user is incorrect. This feature is available after MouseUX is enabled, with this feature, deletion of person is as simple as right-clicking on the target of interest and choose "delete" on the context menu.
    * **Credit:** This feature is build on top of the Delete Command from the original [AddressBook Level-3](https://se-education.org/addressbook-level3/).


  * **New Feature 4**: General Display window ([#83](https://github.com/AY2122S2-CS2103T-W12-2/tp/pull/83) [#105](https://github.com/AY2122S2-CS2103T-W12-2/tp/pull/105) [#109](https://github.com/AY2122S2-CS2103T-W12-2/tp/pull/109))
    * **What it does:** Allow user to see the result of operation more intuitively and to perform further actions directly. This feature is essentially extended from **New Feature 2** above, as the profile display now resides within general display, but general display can show other things if profile display is not needed. 
    * **Justifications:** Outcome from user operation can only be seen from result display window as plain texts previously. This feature provides more intuitive graphical representation that is applicable to i) view profile, ii) see list of tags and iii) copy result from Grab Command. 
    * **Credit:** Grab Command is implemented by [Teoh Jun Jie](https://github.com/junjieteoh).


  * **New Feature 5**: Filter through tag list ([#123](https://github.com/AY2122S2-CS2103T-W12-2/tp/pull/123))
    * **What it does:** Allow user to filter people by tag directly from the list of tags in **New Feature 4** above.
    * **Justifications:** After user is being presented with a list of all the tags in general display, it would be intuitive to simply click on a tag directly and see all the people with the selected tag. MouseUX does not need to be enabled for this feature.
    * **Highlights:** Together with **New Feature 2** above, a convenient workflow is formed.
    * **Credit:** Filter Command is implemented by [Sim Si Leng](https://github.com/pnutzz-0207).
  

### Code contributed
 * You can find all the code I contributed [here](https://nus-cs2103-ay2122s2.github.io/tp-dashboard/?search=9teMare&sort=groupTitle&sortWithin=title&timeframe=commit&mergegroup=&groupSelect=groupByRepos&breakdown=true&checkedFileTypes=docs~functional-code~test-code~other&since=2022-02-18&tabOpen=true&zFR=false&tabAuthor=9teMare&tabRepo=AY2122S2-CS2103T-W12-2%2Ftp%5Bmaster%5D&authorshipIsMergeGroup=false&authorshipFileTypes=docs~functional-code~test-code~other&authorshipIsBinaryFileTypeChecked=false&tabType=authorship).


### Project management
  * Code reviews and manage pull requests.
  * Assign issues to team members.
  * Manage releases to be published.


### Enhancements to existing features
  * Modified GUI layout to comply better for UNite [#42](https://github.com/AY2122S2-CS2103T-W12-2/tp/pull/42).
  * Enhance/fix [regex rule in email field](https://github.com/9teMare/tp/blob/1aaf542f440d3e6308db34bb3f7ddfde6a0e1b61/src/main/java/seedu/unite/model/person/Email.java#L31).
  * Enhance event handlers in `PersonListPanel` through customized callback function [#194](https://github.com/AY2122S2-CS2103T-W12-2/tp/pull/194).


### Documentation
  * User Guide:
    * Update table of content and command summary [#91](https://github.com/AY2122S2-CS2103T-W12-2/tp/pull/91).
    * Update product screenshots [#125](https://github.com/AY2122S2-CS2103T-W12-2/tp/pull/125).
    * Proofread user guide, make final changes and pdf conversion adjustments [#213](https://github.com/AY2122S2-CS2103T-W12-2/tp/pull/213) [#218](https://github.com/AY2122S2-CS2103T-W12-2/tp/pull/218).
    

  * Developer Guide:
    * Added more use cases and NFRs [#39](https://github.com/AY2122S2-CS2103T-W12-2/tp/pull/39).
    * Added information for profile and switch theme features [#73](https://github.com/AY2122S2-CS2103T-W12-2/tp/pull/73).
    * Added implementation detail for `SwitchThemeCommand` [#89](https://github.com/AY2122S2-CS2103T-W12-2/tp/pull/89) [#218](https://github.com/AY2122S2-CS2103T-W12-2/tp/pull/218).
    * Added implementation detail for `GeneralDisplay` [#218](https://github.com/AY2122S2-CS2103T-W12-2/tp/pull/218).


### Community:
  * Report bugs and implementation suggestions for other teams through [#PED](https://github.com/9teMare/ped/issues).

