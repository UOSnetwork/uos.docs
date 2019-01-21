Commit Message Style Guide
==========================

Based on [Chris Beam's How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/).

Provide a meaningful subject
----------------------------

Provide a meaningful subject in your commit.

Example:

```
Fix missing chain api plugin
```

Separate subject from body with a blank line
--------------------------------------------

Separating subject from body makes it easier for others to glance through your commit.

Example:

```
Fix missing chain api plugin

By default, the config.ini has the plugin = eosio::chain_api_plugin
parameter missing. Adding it commented (#)
```

Limit the subject line to 50 characters
---------------------------------------

Keeping the subject line to 50 characters makes it readable.

Example:

```
Fix missing chain api plugin
```

Capitalize the subject line
---------------------------

Start your subject line with a capital.

Example:

```
Fix missing chain api plugin
```

Do not end the subject line with a period
-----------------------------------------

The 50 character limit -- although not a hard limit -- makes the subject line space precious. Do not put a period at the end as it is unnecessary.

Example:

```
Fix missing chain api plugin
```

Use the imperative mood in the subject line
-------------------------------------------

Imperative means "giving a command or an instruction". Do not use `Fixed`, use `Fix` instead.

Example:

```
Fix missing chain api plugin
```

Wrap the body at 72 characters
------------------------------

Wrap the body of your commit message at 72 characters. This makes reading the message easy.

Example:

```
Fix missing chain api plugin

By default, the config.ini has the plugin = eosio::chain_api_plugin
parameter missing. This commit adds the line commented (#).
```
Use the body to explain what and why vs. how
--------------------------------------------

This [commit from Bitcoin Core](https://github.com/bitcoin/bitcoin/commit/eb0b56b19017ab5c16c745e6da39c53126924ed6) is a great example of explaining what changed and why:

```
commit eb0b56b19017ab5c16c745e6da39c53126924ed6
Author: Pieter Wuille <pieter.wuille@gmail.com>
Date:   Fri Aug 1 22:57:55 2014 +0200

   Simplify serialize.h's exception handling

   Remove the 'state' and 'exceptmask' from serialize.h's stream
   implementations, as well as related methods.

   As exceptmask always included 'failbit', and setstate was always
   called with bits = failbit, all it did was immediately raise an
   exception. Get rid of those variables, and replace the setstate
   with direct exception throwing (which also removes some dead
   code).

   As a result, good() is never reached after a failure (there are
   only 2 calls, one of which is in tests), and can just be replaced
   by !eof().

   fail(), clear(n) and exceptions() are just never called. Delete
   them.
 ```

Having a proper explanation saves a lot of time for the developer community to review and understand the change. This ultimately accelerates the development of U°OS.

Include issue number
--------------------

Include the issue number to automatically link it to the tracker. Again, this saves a lot of time in reviewing and understanding your change.

Use the following:

* `Fixes #1234567` -- This will link the issue referenced in the commit message.

Example:

```
Fix missing chain api plugin

By default, the config.ini has the plugin = eosio::chain_api_plugin
parameter missing. This commit adds the line commented (#).

Fixes #1234567
```
