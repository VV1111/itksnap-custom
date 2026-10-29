# ITK-SNAP 4.4 — custom build with AI edit mode

This is [ITK-SNAP](http://www.itksnap.org) 4.4.0 with two changes for AI-assisted segmentation with [nnInteractive](https://github.com/MIC-DKFZ/nnInteractive):

1. **AI edit mode** — three buttons (**Add / Refine / Replace**) in the AI section of the Paintbrush and Polygon tools decide what an AI correction may erase. In official ITK-SNAP, every AI correction erases all voxels of the active label that are not in the newest prediction, so a second correction can cut gaps into the first result. See [AI edit modes](https://vv1111.github.io/guidance/itksnap-dls/edit-modes) for exactly what each mode keeps.
2. **English interface by default** — official ITK-SNAP follows the system language. This build stays in English; use `--lang zh_CN` (or another code) for a translation.

Everything else is unchanged from ITK-SNAP 4.4.0.

## Download

Packages for Windows, macOS (Apple silicon) and Ubuntu 24.04+ are on the [Releases page](https://github.com/VV1111/itksnap-custom/releases). They are built by GitHub Actions from the `feature/dls-edit-mode` branch. The macOS package is not code-signed: right-click → **Open** on first launch. There is no ready-made package for Intel Macs — see [Building](#building).

## Branches

| Branch | Contents | Use it for |
| --- | --- | --- |
| `feature/dls-edit-mode` (default) | ITK-SNAP 4.4.0 + AI edit mode + English default + build workflow | The custom ITK-SNAP — the main branch |
| `baseline-4.4.0-ci` | Unmodified ITK-SNAP 4.4.0 + the same build workflow (Windows only) | An official-equivalent build, for comparing with the custom one |

## AI server

ITK-SNAP is only the client. The AI runs in a separate [itksnap-dls](https://github.com/pyushkevich/itksnap-dls) server on a computer with an NVIDIA GPU. The edit-mode buttons work with any standard itksnap-dls server; nothing changes on the server side.

Installation for each system and how to run your own server: [Install & setup](https://vv1111.github.io/guidance/itksnap-dls/install).

## Building

`.github/workflows/build.yml` builds the Windows, macOS (Apple silicon) and Ubuntu packages on GitHub Actions. To build your own copy:

1. Fork this repository.
2. For an Intel Mac, add `macos-15-intel` to the `os:` list in `.github/workflows/build.yml` (its settings are already in the file).
3. In the **Actions** tab, run **Build custom ITK-SNAP** on the `feature/dls-edit-mode` branch.
4. Download the package from the run's **Artifacts** (kept for 90 days). The first run takes 1–3 hours while ITK and VTK are compiled.

To build locally, follow the [official instructions](http://www.itksnap.org/pmwiki/pmwiki.php?n=Documentation.BuildingITK-SNAP) (ITK 5.4.0, VTK 9.3.1, Qt 6.8.1).

---

ITK-SNAP README
-----------------

### Welcome!

Thank you for your interest in ITK-SNAP! By using this program you are joining
an ever growing community of users from research labs around the world.
ITK-SNAP is an open-source software application made possible by the
committment of dedicated developers, who often make contributions on a
volunteer basis. Original development of ITK-SNAP was supported by the U.S.
National Library of Medicine through PO 467-MZ-202446-1. Subsequent
development of ITK-SNAP version 2.0 has been supported by the U.S. National
Institute of Biomedical Imaging and BioEngineering and the NIH Blueprint for
Neuroscience through grant 1 R03 EB008200-01. Development of ITK-SNAP versions
3.0 - 3.6 has been supported by the NIH grant 1R01 EB014346. 

ITK-SNAP is the result of over 20 years of work by many researchers, software
engineers and students. Please visit the [Credits page](http:/itksnap.org/credits.php) 
to learn about the team that made ITK-SNAP possible!

### Please remember to cite ITK-SNAP

Citations in published work is the best way for us to gauge ITK-SNAP impact.
As of the Summer of 2024, ITK-SNAP has been cited by [over 8000 papers](https://goo.gl/YoM9EK). 
If you use ITK-SNAP for a publication, please cite the paper below.

* Paul A. Yushkevich, Joseph Piven, Heather Cody Hazlett, Rachel Gimpel Smith,
  Sean Ho, James C. Gee, and Guido Gerig. User-guided 3D active contour
  segmentation of anatomical structures: Significantly improved efficiency and
  reliability. Neuroimage. 2006 Jul 1; 31(3):1116-28. 

### Getting Started 

ITK-SNAP was designed for ease of use. There are several resources to get
started with it. 

*   If you downloaded ITK-SNAP as a binary executable from
    [itksnap.org](http://www.itksnap.org/download/snap), you can get started
    by reading the [online tutorials](http://www.itksnap.org/pmwiki/pmwiki.php?n=Documentation.HomePage).
*   If you downloaded ITK-SNAP source code, please follow these [online
    instructions](http://www.itksnap.org/pmwiki/pmwiki.php?n=Documentation.BuildingITK-SNAP)
    to compile and build ITK-SNAP.
*   You will need a 3D image to use this software. Images with which ITK-SNAP
    is known to work are found on the [ITK-SNAP download page](http://www.itksnap.org/download/snap)
*   There are also materials (images, exercises, video) from training courses
    available on the [documentation page](http://www.itksnap.org/pmwiki/pmwiki.php?n=Documentation.SNAP3). 

### Asking Questions

If you have a question about ITK-SNAP, here are the places where you may find an answer. Keep in mind that since ITK-SNAP in not a commercial product, it may take some time for an answer to arrive.

*   If you have an question about how to use SNAP or why it's not doing what
    it should, post in on the [ITK-SNAP Users' List](http://www.itksnap.org/pmwiki/pmwiki.php?n=MailingLists).
*   If you have a technical question or a questing related to ITK, join the 
    [ITK Users' Mailing List](http://www.itk.org/HTML/MailingLists.htm) and
    post your question there.

### Get Involved!

Your participation as a user, developer or sponsor is essential to ensuring a
bright future for ITK-SNAP. There are many ways in which you can contribute to
the stability and quality of this program:

*   By participating in the [ITK-SNAP User and Developer Mailing Lists](http://www.itksnap.org/pmwiki/pmwiki.php?n=MailingLists).
*   By reporting bugs and suggesting enhancements using the [Bug Tracker](http://www.itksnap.org/pmwiki/pmwiki.php?n=Main.BugTracker).
*   By joining the ITK-SNAP Development Team on [SourceForge.net](http://sourceforge.net/projects/itk-snap) and contributing source code.

