---
title: "Images | secureblue"
description: "List of available secureblue hardened operating system images"
permalink: /images
---

# Images

## Table of Contents
{: #table-of-contents}
- [Security recommendation](#security-recommendation)
- [Desktop](#desktop)
  - [Stable](#stable)
  - [Experimental](#experimental)
- [Server](#server)


## [Security recommendation](#security-recommendation)

GNOME and Sway (Silverblue and Sericea images, respectively) secure privileged Wayland protocols like screencopy. This means that on environments outside of GNOME and Sway, applications can access screen content of the entire desktop. This implicitly includes the content of other applications. It\'s primarily for this reason that Silverblue and Sericea images are recommended. A commit submitted by secureblue to fix this in KDE is scheduled to land in Plasma 6.4. Cosmic has <a href="https://github.com/pop-os/cosmic-comp/issues/970">plans</a> to fix this. 

In addition, GNOME also provides weak <a href="https://gitlab.gnome.org/GNOME/gnome-desktop/-/issues/213">thumbnailer sandboxing</a> in Gnome Files, which is an effort to mitigate <a href="https://scarybeastsecurity.blogspot.com/2016/11/0day-exploit-compromising-linux-desktop.html">attacks via thumbnailers</a>. No environment aside from GNOME provides any thumbnailer sandboxing.

This is a relative recommendation between the desktop environments available on secureblue. GNOME and Sway have some extra security niceties like the ones listed above. However, this should not be misconstrued as saying that either one solves any of the fundamental issues with desktop Linux security. For more details, consult the table below.

<div class="table-wrapper">
  <table>
    <thead>
      <tr>
        <th>DE/WM</th>
        <th>Secures privileged Wayland protocols?</th>
        <th>Thumbnailer sandboxing?</th>
        <th>Stability</th>
        <th>Recommendation</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>GNOME</td>
        <td>Yes</td>
        <td>Weak</td>
        <td>Stable</td>
        <td>Recommended</td>
      </tr>
      <tr>
        <td>KDE Plasma</td>
        <td>No</td>
        <td>None</td>
        <td>Stable</td>
        <td>Not recommended until Plasma secures privileged Wayland protocols (ETA: Plasma 6.4)</td>
      </tr>
      <tr>
        <td>Sway</td>
        <td>Yes</td>
        <td>None</td>
        <td>Stable</td>
        <td>Recommended for tiling WM users</td>
      </tr>
      <tr>
        <td>COSMIC</td>
        <td>No</td>
        <td>None</td>
        <td>Experimental</td>
        <td>Not currently recommended</td>
      </tr>
    </tbody>
  </table>
</div>

## [Desktop](#desktop)

<b>nvidia-open</b> images are recommended for systems with NVIDIA GPUs Turing or newer. These include the new <a href="https://github.com/NVIDIA/open-gpu-kernel-modules">open kernel modules</a> from NVIDIA, not Nouveau.<br><b>nvidia</b> images are recommended for systems with NVIDIA GPUs Pascal or older. These include the closed kernel modules from NVIDIA.

### [Stable](#stable)

#### Silverblue (GNOME)

<div class="table-wrapper">

| Name                                      | Base      | NVIDIA Support          |
|-------------------------------------------|-----------|-------------------------|
| `silverblue-main-hardened`                | Silverblue| No                      |
| `silverblue-nvidia-hardened`              | Silverblue| Yes, closed drivers     |
| `silverblue-nvidia-open-hardened`         | Silverblue| Yes, open drivers       |

</div>

<div class="table-wrapper">
  <table>
    <thead>
      <tr>
        <th>Name</th>
        <th>Base</th>
        <th>NVIDIA Support</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><code class="language-plaintext highlighter-rouge">silverblue-main-hardened</code></td>
        <td>Silverblue</td>
        <td>No</td>
      </tr>
      <tr>
      <td><code class="language-plaintext highlighter-rouge">silverblue-nvidia-hardened</code></td>
        <td>Silverblue</td>
        <td>Yes, closed drivers</td>
      </tr>
      <tr>
        <td><code class="language-plaintext highlighter-rouge">silverblue-nvidia-open-hardened</code></td>
        <td>Silverblue</td>
        <td>Yes, open drivers</td>
      </tr>
    </tbody>
  </table>
</div>

#### Kinoite (KDE Plasma)

<div class="table-wrapper">

| Name                                      | Base      | NVIDIA Support          |
|-------------------------------------------|-----------|-------------------------|
| `kinoite-main-hardened`                   | Kinoite   | No                      |
| `kinoite-nvidia-hardened`                 | Kinoite   | Yes, closed drivers     |
| `kinoite-nvidia-open-hardened`            | Kinoite   | Yes, open drivers       |

</div>

#### Sericea (Sway)

<div class="table-wrapper">

| Name                                      | Base      | NVIDIA Support          |
|-------------------------------------------|-----------|-------------------------|
| `sericea-main-hardened`                   | Sericea   | No                      |
| `sericea-nvidia-hardened`                 | Sericea   | Yes, closed drivers     |
| `sericea-nvidia-open-hardened`            | Sericea   | Yes, open drivers       |

</div>

### [Experimental](#experimental)

#### COSMIC

<div class="table-wrapper">

| Name                                      | Base                  | NVIDIA Support          |
|-------------------------------------------|-----------------------|-------------------------|
| `cosmic-main-hardened`                    | COSMIC                | No                      |
| `cosmic-nvidia-hardened`                  | COSMIC                | Yes, closed drivers     |
| `cosmic-nvidia-open-hardened`             | COSMIC                | Yes, open drivers       |

</div>

## [Server](#server)

{% include alert.html type='note' content='After you finish setting up your <a href="https://fedoraproject.org/coreos/">Fedora CoreOS</a> installation, you will need to disable <code>zincati.service</code> before rebasing to securecore.' %}

<div class="table-wrapper">

| Name                                      | Base      | NVIDIA Support          | ZFS Support |
|-------------------------------------------|-----------|-------------------------|-------------|
| `securecore-main-hardened`                | CoreOS    | No                      | No          |
| `securecore-nvidia-hardened`              | CoreOS    | Yes, closed drivers     | No          |
| `securecore-nvidia-open-hardened`         | CoreOS    | Yes, open drivers       | No          |
| `securecore-zfs-main-hardened`            | CoreOS    | No                      | Yes         |
| `securecore-zfs-nvidia-hardened`          | CoreOS    | Yes, closed drivers     | Yes         |
| `securecore-zfs-nvidia-open-hardened`     | CoreOS    | Yes, open drivers       | Yes         |

</div>
