# Curriculum Specifications

Curriculum specifications are the invariant of the Open Source Curriculum Project (i.e. anyone working on the OSCP
will eventually work with curriculum specifications). Curriculum specifications define all of the information encapsulated
by a specific project curriculum, including concept overviews, tasks and instructions, test cases and more. Following
below is the most recent update of how curriculums are defined:

## Version 0.01

This is the initial, extremely rough, work in progress specification for curriculums. A distinction should be made between two main types of curriculums: project based and article based. Project based curriculums are based around a series of tasks that contribute to an overarching project. All concepts are learned as students complete tasks along the way. Article based curriculums present all their concepts in text in order (think textbooks, slides, notes). The eventual goal of this project is to build a specification that accounts for both of these types of curriculums, but initially the focus will be on project based ones.

For project curriculums, the goal is to create a "guided project", that provide just the right ammount of starter code and boilerplate to get a student engaged in the most intellectually stimulating pieces of a certain topic, avoiding the most tedious and unnescessary portions. These projects are separated into different stages, with each successive stage introducing addition starter code and boiler plate once a student has completed the tasks for the previous stage.

### Project Repositories

An example guided project curriculum repository can be found [here](https://github.com/codingandcommunity/sample-curriculum). 
When you take a look at it on GitHub, it may look a bit like this

![coding and community logo](imgs/stages.png)

Note that the various stages of the project are represented by [Git submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules). Each module links to a particular branch in the project repository, corresponding to that stage. Note that 
the actual [project repository](https://github.com/codingandcommunity/sample-app/) that the curriculum is based off of is external to the curriculum repository.

When a project specification is completed, it can be forked into the [Spaceport Curriculums](https://github.com/spaceport-curriculums) organization. Make sure that the project has a good description and has a single topic set to the primary language of the project. Copilot and the Spaceport website will use the Github API endpoint to find [organization repositories](https://developer.github.com/v3/repos/#list-organization-repositories) to populate lists of available projects with a name, description, and thumbnail based off of the topic.

### Copilot Markdown

The content shown to the user in the sidebar (instructions, descriptions, etc.) will be loaded from Markdown files with a few special additions.

#### Example:

Code:
```
#include <stdio.h>
#include <stdlib.h>

int main() {
  int x, y, sum;
  
  /// STEP 1
  /// Use scanf here to read in two numbers to x and y!
  
  printf( "%d", sum ); 
  return 0;
}

```
Markdown:
```
---
title: Step 1
next: step_2.md
prev: introduction.md
jumpto: @STEP 1
---
Given a variable declaration `int x` we can use `scanf("%d", x)` to a read an integer from
the console and assign it to x. Use that [here](@STEP 1) to read in two integers, compute the sum,
and assign it to `sum`!
```

#### Header Tags
* ```title```: Title to display in sidebar
* ```next```: A next button will be shown in the sidebar and will load the specified file when clicked.
* ```prev```: ''
* ```jumpto```: Line or label to jump to when the markdown is loaded

#### Special Comments and Tags

* Instructional Block: Instructional blocks are multiline comments that whose lines start with any of the following:
  ``` 
  ///
  ###
  ```
  For example:
  ```
  /// EXAMPLE
  /// This is an 
  /// instructional block
  
* Code links: The first line of each instructional block acts as a label that can be used in sidebar instructions. For example in the instruction markdown we can put:
  ```
  [link text](@EXAMPLE)
  ```
  to create a link to the instructional block in the code itself. If there are multiple instructional blocks with the same label, we can distinguish between them by adding #<order of occurence>, e.g. 
  ```
  [link text](@EXAMPLE#2)
  ```

### Project Task Specifications

### Concept Specifications
