# Course Awards Medal plugin for Moodle 2.x

Course Awards: A quick and easy way of getting a course's rating from students, awarding courses medals based on score, and reporting on courses Moodle-wide.

This '[medal](https://github.com/vaughany/moodle-block_courseawards_medal)' block: Used to award a medal to the course to recognise it's level and therefore quality.

> **See also:** the '[vote](https://github.com/vaughany/moodle-block_courseawards_vote)' block and the [report](https://github.com/vaughany/moodle-report_courseawards).

## News: Highlighted in May 2012 OFSTED Good Practice report

The Course Awards plugins have been highlighted in a May 2012 OFSTED Good Practice report into South Devon College, alongside Moodle itself. (Look out for 'Moodle Medals' as it's known locally.)

* [OFSTED web page](http://www.ofsted.gov.uk/resources/good-practice-resource-making-most-of-information-and-communication-technology-south-devon-college)
* [PDF](http://www.ofsted.gov.uk/sites/default/files/documents/surveys-and-good-practice/s/South%20Devon%20College%20-%20Good%20practice%20example.pdf)

## Introduction

The Course Awards plug-in system consists of two blocks ('Vote' and 'Medal') and a report. Its purpose is to easily collect user feedback about a course with appropriate back-end reporting.

It is probably a good idea to fully read through this readme before embarking on any installation or bug reporting.

## Licence

Course Awards Medal block for Moodle 2, &copy; 2013 Paul Vaughan.

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program.  If not, see <http://www.gnu.org/licenses/>.

## Purpose

The Course Awards blocks and report form part of a much larger Moodle course rating system (called Moodle Medals) which is used to recognise good practice on Moodle courses and also provide targets for course development. Learner feedback is used to inform medals awarded, however a course must also meet or exceed other criteria to gain a medal. The Bronze medal has basic criteria which must be met, the Silver medal has moderate criteria and the Gold medal has quite strict criteria.  The criteria themselves and how they are judged is performed by staff manually: this plugin is used to inform one aspect of that process.

Irrespective of this, the blocks and report can still be used to gain useful feedback from students about Moodle courses.

## The Medal Block

![Admin view of the Medal block, when a medal has been awarded](http://commoodle.southdevon.ac.uk/file.php/2/course_awards_images/medal-gold.png "Admin view of the Medal block, when a medal has been awarded") ![Admin view of the Medal block](http://commoodle.southdevon.ac.uk/file.php/2/course_awards_images/medal-none.png "Admin view of the Medal block")

The medal block is for use by administrators only. When added to a course, it presents options to add one of the three medals or single achievement ribbon available, or remove one if it has already been awarded. It also shows a history of previously awarded/removed medals. If no medal has been awarded, the block is hidden from students and teachers.

The Medal block allows Admins *only* to award the course with a gold, silver or bronze medal, or an 'achievement' ribbon. This is a manual process as the awarding of the medals is based on the score from the Vote block **as well as a number of other factors about the course determined externally to Moodle**.
Anyone can see the medal once it has been awarded, as long as the Medal block is visible on the course.

## Installation

Installation is a matter of copying files to the correct locations within your Moodle installation, but it is always wise to test new plugins in a sandbox environment first, and have the ability to roll back changes.

> **Note:** The [Vote](https://github.com/vaughany/moodle-block_courseawards_vote) block is a prerequisite for the installation of the Medal block. If the Vote block is not installed, installation of the Medal block will not be possible.

Download the archive and extract the files, or [clone the repository from GitHub](https://github.com/vaughany/moodle-courseawards/). You should see the following files and structure:

    courseawards_medal/
    |-- admin_medal.php
    |-- admin_unmedal.php
    |-- block_courseawards_medal.php
    |-- db
    |   |-- access.php
    |   `-- install.xml
    |-- gpl-3.0.txt
    |-- img
    |   |-- medal_achievement.png
    |   |-- medal_achievement_sm.png
    |   |-- medal_bronze.png
    |   |-- medal_bronze_sm.png
    |   |-- medal_gold.png
    |   |-- medal_gold_sm.png
    |   |-- medal_silver.png
    |   `-- medal_silver_sm.png
    |-- lang
    |   `-- en
    |       `-- block_courseawards_medal.php
    |-- libmedal.php
    |-- pix
    |   `-- icon.png
    |-- readme.md
    |-- settings.php
    |-- styles.css
    `-- version.php

* Create a folder in your Moodle's '**blocks**' folder called '**courseawards_medal**' and place the above files into it. Do not create subfolders.

* Log in to your Moodle as Admin and click on Notifications on the Admin menu.

* The block should successfully install. If you receive any error messages, please [raise an issue on GitHub](https://github.com/vaughany/moodle-courseawards/issues).

## Using the Medal Block

* Go to a course as Teacher role or better.
* Turn on editing and add the 'Course Award - Medal' block and move it where you wish.
* *Administrators* can now award a medal.
* Delete the block in the usual manner.

> **Note:** If you remove the block, the data is retained. Simply re-add the block to get the data back.

### Save as CSV

This option appears on all pages where there is a table of data relating to courses or users. Use it to save the results out as a CSV file, which can then be opened with your favourite spreadsheet or word processing application.

> **Note:** If two admins are generating reports concurrently, the CSV file will be overwritten by the most recently generated report.

## Configuration of the Medal block

The Medal block configuration options can only be changed by a site Admin, and affect the block throughout the whole site.

### Medal image size

The only configuration option is the size of the images. The default setting is *regular* and the default images are 100px (pixels) high. The only other option (currently) is *small*, where the images are 50px high, half the size of the regular images.

> **Note:** You do not have to stick to these sizes: any correctly named image will work, regardless of it's width or height.

## Changing who can Administrate the block

Installing the block gives Moodle a new capability:

* Administer the *Course Awards Medal* block: `block/courseawards_medal:admin`

> **Note:** Think of capabilities as rules which govern how Moodle decides who can do things.

Also, the capability was specifically assigned to these roles:

* The 'administer' capability is assigned to the *Administrator* role.

So when you install the block, only Admins can administrate the block. This works well as a default, but you can make changes if you wish by assigning the above capability to a different role.

> ***Important:*** Teachers can still add and remove the Medal block, just as they can with any block, however this does not mean that the medals already awarded will be lost. If a Medal block is removed, just add it again, and any medals awarded will reappear.

> **Note:** *Uninstalling* the plugin drops the database tables and removes all the awarded medals data for good.

## Code and Image Changes

Some aspects of the block can be changed but this cannot be achieved though configuration, and will require changes to the code. A good code management and versioning system, such as Git, is highly recommended.

### Replacing the Images

It is quite possible to replace the default images with those of your own choosing:

* In '*blocks/coursewards_medal/*' there is an '*img/*' folder containing images.
* Replace these images with your chosen images.
* To avoid having to change the code, save new images over the existing images. Do not use new names.

> **Note:** You may want to make copies of the images before you change them so you can restore them later.

> **Caution:** The code does not specify any widths or heights for images, so that you can use your own and they do not have to be the same size as the default images. However, it is not recommended to go too much wider than the default images as you may start experiencing layout problems with your columns. Experiment.

## Known Issues

* Report:
  * Issue with [MSSQL not having a 'LIMIT' clause](https://github.com/vaughany/moodle-courseawards/issues/2).

Should you find a bug, please [log an issue in the tracker](https://github.com/vaughany/moodle-courseawards/issues) or fork the repo, fix the problem and submit a pull request.

## To Do

* Currently the reports are available to Admins only. Moodle now differentiates between site reports and course reports, so a teacher-accessible course report is on the agenda for the next version.
* Looking at the old Mods and Plugins database entry for 'Course Awards for Moodle 1.9', someone commented that clicking on a star image may not be the most accessible way of using the block, citing issues with colour-blindness and the colours potentially lacking meaning to some. The commenter also suggested some improvements so I will look into this for the next release.
* Some of the larger language string references use underscores (`admin_error`) and others use dashes (`admin-error`). For less future headaches, this should be changed. Preference is underscores.
* Logging of use of the admin reports was around in the 1.9 version, so I should probably add it back in again. For completeness' sake, if nothing else.

Suggestions for features or submissions of non-en language packs are most welcome.

## History

**January 25th 2013 - Blocks**

* Version bump for Moodle 2.4
* Build 2013012500

Tested successfully against Moodle 2.4.1.
Added the capability 'addinstance' to both blocks.

**October 11th 2012**

* Version bump for Moodle 2.x
* Build 2012101100

No major changes, just added icons and a copy of the GPL 3.0, and version bump.

**May 17th 2012 - Vote Block**

* Version 2.0.2 for Moodle 2.x
* Build 2012051700

Fixed an issue whereby a variable double-quoted in a SQL snippet failed in MS SQL and was considered a column name.

Also, changed code where required to meet Moodle's coding guidelines (using the local Codechecker) but no changes to how the code works.

**March 19th 2012 - Medal Block**

* Version 2.0.1 for Moodle 2.x
* Build 2012031900

Fixed some errors with the Medal block, added two new features:

* Fixed a redirect bug when awarding a medal (it would redirect to the main page)
* Added 'Awarded on' and date when a medal is awarded
* Added admin option to change size of pictures between regular (the default at 100px high) and small (50px high)
    * ...which necessitated adding smaller versions of the default images and an admin config page

**February 8th 2012 - Whole System**

* Version 2.0 for Moodle 2.x
* Build 2012020800
