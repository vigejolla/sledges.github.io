---
title: Sailfish_OS_Source
permalink: Services/Development/Sailfish_OS_Source/

---

## Sailfish OS Source

Please see [Sailfish OS Architecture](/Reference/Architecture) for a
comprehensive list of the various components which make up the Sailfish
OS stack, including links to the source repositories for those
components.

Here is a table that contains the information about different code
locations, how to get an account and what is the contribution policy.

<table>
<thead>
<tr class="header">
<th><p>|Location</p></th>
<th><p>| Description</p></th>
<th><p>| How to get an account</p></th>
<th><p>| How to contribute</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://git.sailfishos.org/">https://git.sailfishos.org/</a></p></td>
<td><p>Sailfish OS Core source code repositories</p></td>
<td><p>Account can be created by asking lbt or sage at #sailfishos IRC channel at Freenode</p></td>
<td><p>Contributions done by <strong>forking the git tree</strong> (https://git.sailfishos.org/help/gitlab-basics/fork-project.md) and <strong>creating a merge request</strong> (https://git.sailfishos.org/help/gitlab-basics/add-merge-request.md).<br />
<br />
<strong>NOTE:</strong> Only repository maintainers can do pull requests from a branch of the main git tree.<br />
<br />
<strong>NOTE:</strong> For each repository git submodules must be using https urls.<br />
<br />
If you would like to propose a new component/package to be added the core of the OS, you can create pull request containing the addition to one of the <code>packages:</code> sections at <a href="https://git.sailfishos.org/mer-core/Maintainers/blob/master/maintainers.yaml">https://git.sailfishos.org/mer-core/Maintainers/blob/master/maintainers.yaml</a> with the reasoning.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://github.com/sailfishos">https://github.com/sailfishos</a></p></td>
<td><p>Some new Sailfish OS git tree for variaty of different components</p></td>
<td><p>Account can be created at <a href="https://github.com/join">https://github.com/join</a></p></td>
<td><p>Contributions done by <strong>forking the git tree</strong> (https://help.github.com/en/articles/fork-a-repo) and <strong>creating a pull request</strong> (https://help.github.com/en/articles/creating-a-pull-request-from-a-fork).<br />
<br />
<strong>NOTE:</strong> Only repository maintainers can do pull requests from a branch of the main git tree (https://help.github.com/en/articles/creating-a-pull-request).<br />
<br />
<strong>NOTE:</strong> For each repository git submodules must be using https urls.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://github.com/mer-hybris">https://github.com/mer-hybris</a></p></td>
<td><p>Hardware adaptation related git trees</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="https://github.com/mer-tools">https://github.com/mer-tools</a></p></td>
<td><p>Some tools that are usefull in development and are located in separate repository</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="https://github.com/mer-qa">https://github.com/mer-qa</a></p></td>
<td><p>Some tools that are usefull in development and are located in separate repository</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="https://github.com/MeeGoIntegration">https://github.com/MeeGoIntegration</a></p></td>
<td><p>Tools used in the CI and build process, like OBS.</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Closed git trees</p></td>
<td><p>There are some closed git trees for proprietary code</p></td>
<td><p>Accounts created on case by case basis</p></td>
<td><p>Contributions are done with pull requests from branches. Contributor has rights to create branch that has <em>contribution-</em> prefix or company name, i.e., <em>companyname-</em> prefix</p></td>
</tr>
</tbody>
</table>

Please check [contribution
guidelines](/Collaborative_Development#Contributing_The_Change)
and [changelog generation
guidelines](/Building_packages#Changelog_generation) before
actual contribution.

Release specific sourcecode drops can be found from
<http://releases.sailfishos.org/sources/>

### Finding The Source For A Package

There are a variety of ways to determine the location of the source
repository for a particular package:

  - search the git trees mentioned in the table above
  - search the [Core Areas and APIs](/Reference/Core_Areas_and_APIs)
    documentation to find the appropriate repository
  - look hints on the device, e.g.,

If you have developer mode installed you can in terminal search more
detailed information. For example searching packages by name:

`pkcon search name browser`

... and after finding the packag name you can get more details:

`pkcon get-details sailfish-browser`

Same calls can be done also with zypper (zypper not included by default,
and needs to be installed, with `devel-su pkcon install zypper`)

`devel-su zypper se browser`  
`devel-su zypper info sailfish-browser`

If you want to know which package a file belongs to you can check with
`rpm` the package name:

`rpm -qf /etc/gps.conf`

If all other means fail and the package name is known, the contributor
can search for it on <https://build.sailfishos.org/> and then examine
that package's \`\_service\` file to determine the source code
repository.
