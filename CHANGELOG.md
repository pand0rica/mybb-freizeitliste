# Changelog

All notable changes to this plugin are documented in this file.
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Changed (lifecycle)
- Templates are created in `activate()` and removed in `deactivate()` (dev kit `debugging.md`
  #8) instead of `install()`/`uninstall()`. Updating the plugin now only needs
  deactivate/activate to refresh the templates; settings and data are kept.

### Security
- ACP CSRF protection uses MyBB's native mechanism (dev kit `debugging.md` #23): write
  handlers only act on POST and `admin/index.php` validates the `my_post_key` itself –
  no own key check or helper.

### Fixed
- **Mixed action buttons.** Join/leave/save role, approve/reject and the contact removal
  buttons used `<button>` while other actions used `<input type="submit">`. All actions
  now use `<input type="submit" class="button">`; the contact removal button no longer
  wraps a profile link inside a button (invalid HTML). Old `participation_action` posts
  are still accepted.
- Integer columns in WHERE clauses (`id`, `entry_id`, `user_id`, `gid`, `tid`) are no
  longer quoted as strings.

### Changed
- German texts use gender-neutral wording (“Teilnahmeliste”, “Account”, “Ansprechperson”).

## [1.0.0] - 2026-08-17

### Added
- Front-end leisure list (`freizeit.php`) grouping approved activities by category.
- Submission form for members of configurable groups, with a team approval queue.
- ModCP approval queue to approve or reject pending entries and contact changes.
- ModCP contact management (add/remove contacts per activity, via the approval queue).
- Participation: members can join/leave an activity and set an optional role.
- Configurable group permissions for submitting, moderating and viewing participants.
- ACP category management (add, edit, delete, sort) under Configuration.
- Red index alert for team members when items are waiting for approval.
- English and German (deutsch_du) language packs for both front-end and ACP.
