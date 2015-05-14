# iproute2 as a Library: iproute2-lib

This project started as a clone of the iproute2 Kernel Project (index : kernel/git/shemminger/iproute2.git), that attempts to put a linkable library interface onto the iproute2 utility.

## Why

My motivation for creating this project was a way to enable reuse of the vast amount work that has been done to correctly implement the use of the Linux system networking libraries.  

I originally started out writing a grammar based parser for the output of iproute2, but this proved to be daunting as the constructs vary wildly. So, the maybe not so obvious path forward was to use the iproute2 code base directly.

This project is the first pass at that end.  I have no immediate plans to try to submit any of these changs to the iproute project maintainers.  This is really something very specific to a project that I need to undertake, it was an answer to a question - if you will.

## Status

My inital project deliverable is for a system that targets Ubuntu 14.04.  So, all current development is being done against a tag (version-v3.12.0) for the current 14.04 LTS package version.  

   $ lsb_release -a
   No LSB modules are available.
   Distributor ID:         Ubuntu
   Description:            Ubuntu 14.04.2 LTS
   Release:                14.04
   Codename:               trusty

   $ dpkg -l iproute2
   Desired=Unknown/Install/Remove/Purge/Hold
   | Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
   |/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
   ||/ Name               Version         Architecture          Description
   +++-==================-===============-=====================-====================================
   ii  iproute2           3.12.0-2        amd64                 networking and traffic control tools



The project is in a very nascent form currently.  So far I've implemented: 
* the makefile structureal changes for generating a linkable archive library (more on this later).
* the link_desc structure that provides a basic link list of link descriptors
* the ability to populate link_desc from 'ip link list' and 'ip addr list' - and the 'l', 'ls', 'show', equivalents.

## Join

If anyone else finds this interesting, then by all means!  Right now this project addresses my very narrowly scoped needs, I would love to coordinate some effort around making this a viable scale project.

