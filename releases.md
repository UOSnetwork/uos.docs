U°OS Releases
=============

* [Attila 1.1](#attila1_1)
* [Attila 1.2](#attila1_2)
* [Attila 1.3](#attila1_3)
* [Attila 1.4](#attila1_4)
* [Attila 1.5](#attila1_5)
* [Attila 1.6](#attila1_6)
* [Attila 1.7](#attila1_7)
* [Attila 1.8](#attila1_8)

Attila 1.1 <a name="attila1_1"></a>
-----------------------------------

**Date:** November 20, 2018

### U°Community

#### New Features

[U°OS Governance](https://u.community/governance): You can now vote for Block Producers with your Staked tokens (you can edit your stake in your account wallet - a downward arrow sign near your rating in the menu).

### U°OS

#### New Features

* **Dynamic Importance-based emission:** Dynamic emission implemented, which is distributed in accordance to account's Importance
* **Transfer activity metering in Importance calcucation:** Transfer activity is now considered when calculating account Importance

#### Bug Fixes

* Fixed wrong links in community post notifications
* Fixed autocapitalized first letters in display name
* Fixed 500 Error when accepting community invitation
* Fixed endless loop in New notifications
* Fixed userpic upload bug
* Fixed media-post picture size
* Fixed media-post date being refreshed after upvote

Attila 1.2 <a name="attila1_2"></a>
-----------------------------------

**Date:** November 27, 2018

### U°Community

#### New Features

[Account Registration v 1.2](https://u.community/registration):

* Username selection tooltips
* Additional entropy during Brainkey generation via pointer movement
* Brainkey verification via randomly positioned textboxes

**Basic Post Picture Upload:**

* Pictures can now be uploaded into basic posts

### U°OS

#### New Features

* **Transaction caching**
* **Account balance metering in Importance calculation:** Account balance is now considered when calculating account Importance

#### Bug Fixes

* Fixed bold font in basic posts
* Fixed bold font in H2 media-posts
* Fixed Buy RAM price calculation multiplier
* Fixed upvote notifications’ text
* Fixed media-posts title and lead text character limit
* Fixed user wallet texts
* Fixed oldest content being shown first in user and community profiles
* Fixed pagescroll for low resolutions

Attila 1.3 <a name="attila1_3"></a>
-----------------------------------

**Date:** December 5, 2018

### U°Community

#### New Features

**Account transactions activity log:**

* Added a list of transactions in user account menu
* Transactions are categorised by actions

**Posts now have a direct link:**

* Added post publication date and time  
* Link can be copied by clicking on the post time
* Clicking on publication date now opens a post preview popup

**Post updates:**

* Added newline in posts and comments via "Enter", publish via "CMD-SHIFT"
* Added an "edit post" button

### U°OS

#### New Features

Added infrastructure for quick Importance algorithm research, testing and deployment.

#### Bug Fixes

* Fixed the key combination "CMD-SHIFT" creating an empty post
* Fixed authorization popup scroll being blocked on some devices
* Fixed Governance not being available for mobile and other small screen devices
* Fixed edited not being published in some cases
* Fixed brainkey verification numbers not representing textboxes

Attila 1.4 <a name="attila1_4"></a>
-----------------------------------

**Date:** December 12, 2018

### U°Community

#### New Features

**Account activity log:**

* Added "emission" transaction type
* Added a popup with raw transaction information

**Publications categories:**

* Added test categories: hot, trending, fresh
* The "Publications" page now shows posts in a newsfeed format
* Added a list of people and communities, authoring posts in a given category

**Main page articles rotation:**

* Top posts on the main page are now randomly taking the main spot

#### Bug Fixes

* Fixed duplicate entries in the user wallet activity log
* Fixed notifications providing incorrect links to posts in communities
* Fixed post sharing notification not displaying a post preview picture
* Fixed main page top post author rating preview locking to 1000°

Attila 1.5 <a name="attila1_5"></a>
-----------------------------------

**Date:** December 19, 2018

### U°Community

#### New Features

**Publications editor update:**

* Removed separate title, lead text, picture fields
* First line is now used as Title
* First picture is now used as Preview
* Added draft autosave

**Post social thumbnails:**

* Post and publication links now have common thumbnails when pasted into social media 

**Governance revamp:**

* Added UOS network context to BP voting
* Added Governance description
* Added your stake display and edit feature to the Governance page
* Added voting rules display on voting page
* Added new voting pipeline

**Other features:**

* Added "show more" on "People" page
* Added account name search and display when sending tokens
* "Hot" tab on "Publications" page is now active by default for mobiles
* Added user communities list on the main page

#### Bug Fixes

* Fixed empty posts in communities

#### GitHub

* Added backend docker configs for easy installation

### U°OS

**Importance voting:**

* All accounts are now voting with their integral account Importance

Attila 1.6 <a name="attila1_6"></a>
-----------------------------------

**Date:** December 29, 2018

### U°Community

#### New Features

**Server-side rendering:**

* Page pre-rendering on the server 
* Faster page loading
* Search engine-friendly content

**Tagging system:**

* Automatic tag parsing
* Automatic tag links
* Tag page
* Tag rating system
* Direct posts from tag page

**Publication draft:**

* Content you’ve entered is now autosaved until published

### U°OS

**Social Index Algorithm update:**

* Communities' start rate is now 0
* Interactions are now calculated directly between accounts
* Actions fade out faster

Attila 1.7 <a name="attila1_7"></a>
-----------------------------------

**Date:** January 16, 2019

### U°Community

#### New Features

**User search**

* Added simple search to the people page: https://u.community/users
* Added pagination to search results.
* People can be looked up by account or displayed name.

Attila 1.8 <a name="attila1_8"></a>
-----------------------------------

**Date:** January 23, 2019

### U°Community

#### New Features

**Mention system:**

* Added user search popup in any content editor, called by pressing `@`
* Added notifications on user mentions
* Added links to mentions

**Publication preview settings:**

* Added a popup with preview settings
* Added a separate preview thumbnail upload feature
* Added a dropdown menu with community picker

**Account-based user profile links:**

* Added new user profile page link format: https://u.community/users/
* Added share button to publication page

**Migrated backend source code to TypeScript**

* Added ESlint

**Added web-app monitoring service**
