# Rails Style Guide

## Architecture

- See [Example stack for a command in Rails](https://gist.github.com/nicholasjhenry/401621e0637ea372242b)
- Separate "Management" modules (e.g. Device Management, Fluid Management)
- Add 'standard' System module for User, Session, Tenant etc.
- Define aggregate roots
- No circular dependencies between aggregate roots
- Design Domain model using [Modelling in Colour](http://www.step-10.com/SoftwareDesign/ModellingInColour/) method

## Controllers

- explicitly pass local vars to view/templates (see http://thepugautomatic.com/2013/05/locals/)
