---
layout: default
title: "PE 2015.2 » Puppet Enterprise Version Numbers"
subtitle: "Puppet Enterprise Version Numbers"
canonical: "/pe/latest/pe_versioning.html"

---

Beginning in July 2015, Puppet Enterprise is moving to a new versioning system. The new versioning scheme will follow a familiar "x.y.z" pattern, where "x" reflects the year of the release, "y" reflects the ordered number of the release within the year, and "z" reflects a patch/bugfix release.

For example, because the next release of Puppet Enterprise will be our second of 2015, it will be referred to as Puppet Enterprise 2015.2, and a hypothetical patch release would be 2015.2.1. Similarly, the first 2016 release of Puppet Enterprise will be referred to as Puppet Enterprise 2016.1. Puppet Enterprise does not use semver (semantic versioning).

We are making this change to align with our engineering and release cadence for Puppet Enterprise, which is based on time, rather than the volume of features. Additionally, time-based versioning makes it easier for you to quickly determine how current your version of Puppet Enterprise is.

We do not plan to change version numbers for previously released editions of Puppet Enterprise, such as Puppet Enterprise 3.8.

## Puppet Labs’ Open Source Projects

All of our open source projects — including Puppet, PuppetDB, Facter, and Hiera — use semantic versioning (“semver”) for their version numbers. This means that in an x.y.z version number, the “y” will increase if new features are introduced and the “x” will increase if existing features change or get removed.

Our semver promises only refer to the code in a single project; it’s possible for packaging or interactions with new “y” releases of other projects to cause new behavior in a “z” upgrade of Puppet.

Historical note: In Puppet versions prior to 3.0.0 and Facter versions prior to 1.7.0, we weren’t using semantic versioning.

