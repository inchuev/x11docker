---
title: 'x11docker: Run GUI applications in Docker containers'
tags:
  - docker
  - graphical user interface
  - software development
  - software deployment
  - sandbox
  - reproducibility
  - reproducible research
  - prototyping
authors:
  - name: Martin Viereck
    orcid: 0000-0002-4532-4020
    affiliation: "1"
affiliations:
 - name: Martin Viereck, Germany
   index: 1
date: 22 March 2019
bibliography: paper.bib
---

# Summary

[`x11docker`](https://github.com/mviereck/x11docker) allows to run graphical desktop applications in a 
[GNU/Linux container](https://en.wikipedia.org/wiki/Operating-system-level_virtualization) using 
[Docker](https://en.wikipedia.org/wiki/Docker_(software)).

## About Containers in general

Containerisation in general has proven as a useful technology for packaging applications and their 
dependencies for deployment in cloud-based infrastructures.
A container is similar in usage to a [virtual machine](https://en.wikipedia.org/wiki/Virtual_machine), 
but needs less resources. The technical concept, however, is completely different.

The properties of containers such as portability, dependency packaging, minimal requirements of 
system environment (i.e. only the container runtime), isolation, and version management of complete 
application stacks make it a promising candidate to increase computational reproducibility and 
reusability of research analyses [@boettiger_introduction_2015].
Their use has been demonstrated in various disciplines, such as software engineering research 
[@cito_using_2016], bioinformatics [@hosny_algorun_2016], and archeology [@marwick_computational_2017], 
and their preservation is an active field of research [@rechert_preserving_2017,@emsley_framework_2018].

Software and required libraries can be installed in a Docker image to run software that is difficult 
to install otherwise. It is possible to run outdated versions, specific versions, or latest development 
code side by side.

## About x11docker

The most popular Linux container frontend, Docker, does not provide a 
[display server](https://en.wikipedia.org/wiki/Display_server) that would allow to run applications 
with a [graphical user interface](https://en.wikipedia.org/wiki/Graphical_user_interface) (GUI), 
because Docker is originally built for server software.
`x11docker` fills this gap.

`x11docker` allows to execute [Desktop](https://en.wikipedia.org/wiki/Desktop_environment) GUI applications
in an isolated environment by running an [X display server](https://en.wikipedia.org/wiki/X_Window_System) 
on the host system and providing it to applications in Docker containers.

`x11docker` simplifies container setup and access to host resources like shared files, GPU acceleration, 
audio, webcam and printer. Non-GUI applications can benefit from this, too.

Additionally, `x11docker` does some [security setup](https://github.com/mviereck/x11docker#security) 
to enhance container isolation from host system. 
It follows the [principle of least privilege](https://en.wikipedia.org/wiki/Principle_of_least_privilege).

`x11docker` thereby facilitates quick creation, distribution, and evaluation of research prototypes 
without compromising on a researcher's skills (not imposing browser-based GUI nor requiring 
command-line proficiency), domain (having e.g. established and widely-acknowledged GUI-based tools), 
security, computational reproducibility, or a scholarly review process.

`x11docker` has its own (optional) graphical frontend, `x11docker-gui`, and runs on GNU/Linux. 
Running in a Virtual Linux Machine on MS Windows and macOS is supported. 
With a few limitations it can run natively on MS Windows, too.

# Alternatives to x11docker

A common way to allow GUI applications in containers is by providing a web server within the container 
and rendering an HTML-based GUI in a common web browser, e.g. as jupyter notebooks [@jupyter2018binder]. 
Further possibilities are an xrdp server, VNC server, SSH server or xpra server within the container.
These solutions require some specific setup and provide a rather slow interaction due to a lot of 
network data transfer.

# References
