# Development

* [[Development:-Administration-and-Team]]
* [[Development:-Maildir-SyncBack]]
* [[Development:-UTF-8]]
* [[Development:-Releasing-a-new-sup]]

## Useful pages

* [[Running from git]]
* [[Running More Than One Sup At A Time]]
* [[Using RVM for different ruby environments]]
* [[Programmatically Accessing Sups Index]]
* [[Contributing]]
* [[Wishlist]]
* [[Heliotrope and Turnsole]]

## Mailing list
* [sup-devel mailinglist](http://rubyforge.org/pipermail/sup-devel/) Development specific talk
* Also subscribe to sup-talk

## Roadmap

## Sup-0.13
* Release sup-0.13 very soon: will _not_ include maildir-syncback support or work on Ruby 2.

## Sup-0.14
* Support Ruby 2.0.0 (milestone 2) and 1.9
* Re-brand to the Sup developers and this infrastructure (issue #20)
* Migrate to Psych (issue #17)
  * Requires a configuration file migration
* Remove all deprecated and abandoned dependencies and components:
  * Iconv (issue #23) ([[Development:-UTF-8]])
  * Switch to Mail from RMail
  * Drop the bad ncursesw gem
* Implement IMAP syncback support ([[Development:-Maildir-SyncBack]])
* Update to version 2 of the gpgme gem
* Get UTF-8 encoding right ([[Development:-UTF-8]])

## Roles and tasks
This list shows who is the main person responsible for each task. The responsibility may be shared and we hope several people will contribute to each:

- Getting a release of sup-0.13 (for ruby 1.8 and ruby 1.9): maintainers
- Managing the 'maildir-sync' branch: @ericweikl + maintainers
- Home page: @jof + maintainers
- Setting up a consistent infrastructure: maintainers
- Managing the 'sup-two' branch: maintainers
