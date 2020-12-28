# Git Branch Model

## Branches

### Main Branch: `master` (or `staging`)

At its core, the development model is heavily inspired by existing models out there. The central repositories each
contain a main branch with an infinite lifetime; for the CMS this is `staging`, for the other projects it is `master`.

Unlike other Git flows published in the wild, Joomla does not support a separate branch for stable releases. This is not
a disadvantage, as all releases get their own tag, which makes it easy to find the appropriate code state. The main
branch thus serves as both `master` and `develop` branch and contains the changes for the next release in addition to
the latest stable release.

So we consider `master` (or `staging`) as the main branch where the source code of HEAD always reflects a state with the
latest development changes applied for the next version. This branch can therefore be called the 'integration branch'.
All automatic nightly builds are produced from here.

When the source code in the main branch reaches a stable point and is ready to be published, a release is
performed, automatically setting a version tag.
See [@todo: Release Cycle] for details on the release procedure.

### Release Branches: `x.y-dev`

Features usually take a long time to develop. Following SemVer, adding a feature also requires increasing the minor
version number (the *y* in *x.y.z*). To still be able to make patch-level changes to the current version, Joomla uses
separate branches for one or more upcoming minor versions and the next major version (to be able to introduce B/C
breaks). These branches are called `x.y-dev`, where *x* and *y* are the major and minor version numbers respectively.

Each `x.y-dev` branch is treated as the main branch for the corresponding release. Once the source code in
the `x.y-dev` branch is stable and ready to be published, it is merged into the `master` (or `staging`) branch. A
release is then performed, automatically setting a version tag.
See [@todo: Release Cycle] for details on the release procedure.
After merging into the main branch, the branch `x.y-dev` is deleted.
