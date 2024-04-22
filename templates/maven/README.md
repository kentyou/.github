# Maven Templates

When developing a Maven-based project, use these templates to remain
consistent with Kentyou best practices.

## POM Files

We split the POM files into two different files, as they serve two different
purposes: Reactor POM and Parent POM.

By splitting these responsibilities into two distinct POM files, we ensure 
that modifications to project structure (like adding or removing modules) 
do not interfere with configuration management. This approach enhances 
clarity, maintainability, and scalability of complex multi-module projects.

### Reactor POM
This file Focuses solely on the structure and build order of the project.
It acts as an orchestrator for building multiple modules. This separation
allows developers to manage the build sequence without mixing up the build
logic with configuration data.

**Purpose**: 
The Reactor POM serves as the root for multi-module projects. It is
used primarily to define the build order and list all sub-modules 
included in the project.

**Usage**:
- Use the template `reactor-pom.xml`.

- Copy this template to your new repository, and rename it to `pom.xml`.

- Be sure to update all placeholder values (values in [brackets]).

- This POM should include only module listings and essential
  build configurations that apply collectively to all modules.

- It should not contain dependency definitions or plugin 
  configurations specific to individual modules.

### Parent POM
This file acts as a central configuration manager. It contains all the
common setup details needed across various modules or projects, such as
plugin configurations and dependency management. This helps in avoiding
duplication and ensures that any changes in the build configuration are
centrally managed and propagated across all child modules.

**Purpose**: 
The Parent POM is designed to provide common configurations for all 
child projects or modules. This includes settings for dependency management, 
plugin configurations, and other properties that promote consistency 
across projects.

**Usage**:
- Use the template `parent-pom.xml`.

- Copy this template to your new repository, and rename as `parent/pom.xml`.

- Be sure to update all placeholder values (values in [brackets]).

- It should define shared configurations such as dependency versions, 
  build plugins, resource filters, and more.

- This POM should be used as the parent in the POMs of all individual 
  modules or projects to ensure a uniform build environment.

## Potential Improvements

Instead of having individual files, we may want to consider having a Maven Archetype.
However, that is quite a bit of overhead for an operation that is so infrequent.