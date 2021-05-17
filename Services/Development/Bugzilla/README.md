---
title: Bugzilla
permalink: Services/Development/Bugzilla/

---

Bugzilla is an issue tracking service developed by Mozilla. Issue
tracking is an essential part of software development, and Bugzilla
provides a means of having a centrally-controlled issue tracker to allow
multiple teams to create and monitor issues for a software product.

Sailfish OS provides the [Mer Bugzilla](https://bugs.merproject.org/)
service for tracking Mer-related issues. Tasks and bugs should be
created here.

The typical lifecycle of a bug or task in Bugzilla is:

1.  A new issue is created in Bugzilla under the relevant area (e.g.
    "Mer Core").
2.  The issue is assigned to a relevant developer, or a developer sees
    the newly reported issue and self-assigns it.
3.  The developer submits the patch(es) to resolve the issue, and marks
    the issue as resolved and fixed. Alternatively, the issue can be
    resolved in Bugzilla as not requiring a fix - for example, if it is
    a duplicate issue, or already fixed, etc.

Here is a list how bug status is usually handled:

|                      |                                                                                                                                                   |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| NEW                  | Bug filed                                                                                                                                         |
| ASSIGNED             | Bug assigned and worked on by certain person, that is defined in Assignee field.                                                                  |
| RESOLVED - COMMITTED | Developer has committed the fix to the git tree and it has been merged to the upstream.                                                           |
| RESOLVED - FIXED     | The fix has landed to the development builds, usually this step is done automatically by the CI if developer used proper "Fixes XYZ\#123" syntax. |
| CLOSED - RELEASED    | Fix has been released in a release.                                                                                                               |

If it is determined that the fix is not sufficient, the issue can be
reopened in Bugzilla. However, it is recommended this is only done for
issues that have not already made it into a release, or issues where the
proposed fix is clearly inadequate. This is to avoid the reopening of
bugs which have associated factors or circumstances that have changed
greatly since the original fixes were submitted, and to avoid confusion
arising from outdated comments in the original Bugzilla issue. It may be
simpler to just create a new issue and include a link to the original
issue.

For convenience, the webhooks for the Mer Bugzilla can automatically
update the status of the bug according to the git commit message in a
patch. See the [Webhooks](/Services/Development/Webhooks) page for more details.
