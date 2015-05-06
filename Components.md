# Components #

## Inguma (Text based) ##

The daily use tool and the most important part of Inguma is the text based console version. All modules should work using the text based version. Well, "should work", remember that is in ALPHA state currently.

Console based interface is planned as a collection of independent tools that share a common knowledge data where they store results, don't expect heavy interaction between these tools neither automation. The main porpuose of console UI is to ofer to the user a collection of tools and libraries within a power enviroment as the interactive python prompt.

## Inguma GUI (PyGtk) ##

As a proof of concept I wrote a graphical toolkit for Inguma, based on pyGtk. Most modules (not all) work in the graphical version but is not as tested as the text based version and many modules, specially those that are using "raw\_input" will not work.

Don't expect to automagically own one Oracle Database Server by clicking. Not at the moment.

## [Krash](Krash.md) - Token based fuzzer ##

Krash is a general purpose network oriented fuzzer. Save a raw packet in a file and the tool will (internally) split it into "tokens" (i.e., automagically find blocks) and will fuzz any token the tool founds.

In fact it is block based fuzzing but a little bit automated.

## [OpenDis](OpenDis.md) Framework ##

Reading assembler may be a tedious task. Reading asm to reverse engineer a (large) binary project is a very tedious task. If you don't have the money to buy one commercial toolkit (IDA Pro...) you finally need a tool that simplifies the task of highlighting error prone blocks and identify variables, blocks, functions, tools to make binary diffs, etc...

OpenDis uses internally "objdump" and "nm". If you're using Linux or Unix (**BSD) you will surely have these tools installed. Under Win32 you need to download these binaries. For example, downloading [MinGW](http://www.mingw.org/) development environment.**

OpenDis is not only a disassembler or assembly language clarifier but a reverse engineering framework. In the latest version, as of Inguma 0.0.6, binaries can be saved as databases. OpenDis databases are [c](c.md)pickle objects you can load and read from simple Python scripts.

## The PyShellcodeLib ##

Comming soon...