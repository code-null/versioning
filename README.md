# **code null versioning 1.0.0.0 (CNV)**

The CNV provides a rather simple schema. It is based on [Semantic Versioning](https://semver.org/), but with a rule set, that is applicable to a broader range of projects.

A version string has the following structure and only consists of numbers. The parts that are in brackets are optional. Every bracket pair can be combined with every other or be left out entirely. But what is inside must always be there. When using these, the meaning must be specified in the README. For that the following destructuring can be used.

Structure: (prefix)w.x.y.z(dot)(dash)(\*)(-S)

Destructured:

- prefix: A prefix like "v" to indicate that is a version number
- w: Use for major versions
- x: Use for smaller functional updates
- y: Use for bug fixes and code optimization that do not impact the functionality and security updates
- z: Use for small styling changes, typo fixes or minor code changes, that do not impact the functionality
- dot: optional dot for separating the next part
- dash: optional dash for separating the next part
- \*: can be a letter or number, to indicate any further changes
- \-S: The current stage of the project (alpha, pre-alpha, etc.)

## **Rules**

The following rules apply when changing the version number. While some points might appear logical, they are still explicitly named.

1. A version number must always go up
   - The same applies to letters if used
2. Increments are only allow in single steps
   - E.g.: No skipping from 1.1.2.0 to 1.1.4.0
3. A project always starts at version 0.1.0.0
4. When increasing a part of a version number, all lower parts must be reset to 0
   - An increase in the stage must reset the version to 0.1.0.0
   - If it is the first complete release the first version starts at 1.0.0.0
5. The stage addition must not be added or removed in the middle of versioning and be either present from the beginning or not at all
   - Exception: If a stable production ready version is released, the stage addition may be dropped
6. A release may contain multiple smaller changes
   - E.g.: a major release may contain bug fixes as well
7. A prefix must not change whatsoever and must be present from the very beginning or not at all
8. All versions with major version 1 or higher are considered production ready, if they have dedicated releases
   - Exception: If the stage is specified in the version string

## Use cases

The code null versioning can be used for the following things:

- Programs
- (REST) Servers
- Packages
- Components
- Documentation files
- Projects
- Websites
- Data Formats/Types (e.g.: .json files)
- Classes
- Schemas
- Interfaces
- Product Designs
- Plans, Flow Charts, etc.

## **Increasing the version numbers**

The following guidelines will help decide whether or not to change the version.

### **Major (w)**

These are released when there was a lot of change in functionality. The comparison base is always the initial release of the previous major version. Example: The current version is 3.3.6.1. A jump to version 4.0.0.0 seems reasonable, thus the changes are compared relative to version 3.0.0.0.

The following cases should always lead to a new major version:

- More than half of the relevant code, text, structure etc. was reworked/refactored
- The UI or design changed drastically (not just different colors, but a (completely) new layout)
- When overflowing from minor version when reaching 10 (3.9.5.0 would become 4.0.0.0 and not 3.10.0.0)
- Breaking changes in any sense were introduced (e.g.: a commonly used interface changed the structure and therefore a lot of other parts needed to be changed, the end user has to change things to keep using the product, code etc.)

If someone ever get the feeling, that what was changed is a lot different from what they had before, it is recommended to make it a new major version, even if it is technically just a new minor version.

For on going projects, that do not have dedicated releases, but rather change over time in small steps, major version increases by overflowing from minor versions.

### **Minor (x)**

These are released when new smaller functionality was added, other changes where made that the end user can notice or a security issue was fixed.

The following cases should always lead to a new minor version:

- A new part was added in software (e.g.: new area in a program/website/blog, additional APIs on a server, new attributes on a component, new class member)
- A new part was added in other cases (e.g.: new section in a document, new arrangement on a floor plan, second handle for a pot))
- Some parts were moved to a different position (e.g.: file input is now at the top instead bottom, section b now comes before section a, the arrangement of buttons on a remote control changed)
- A security issue was fixed

### **Optimization (y)**

This part is increased whenever bug fixes, changes in the (code) structure or other optimization are released. The word "bug" is not strictly meant for coding projects, but also refers to everything else that leads to unwanted behavior or consequences.

The following cases should always lead to a new optimization version:

- One or multiple bugs were fixed
- Code was refactored/optimized, without changing the functionality (e.g.: a function was rewritten to be more efficient)
- Optimization in a product functionality

Some examples for what is considered a bug outside of coding projects:

- The design of a mug leads to dripping when drinking
- A rule in a rule book was too loosely defined and creates a loophole
- In a document a word was used wrongly and changes the meaning of the sentence
- In an Excel table a formula misses some parentheses that result in a different output
- On a website an old link is still present
- On a floor plan the wrong dimensions were used for the placement of an item

### **Style (z)**

Style updates only include very minor changes, that do not impact the product or project in a meaningful way.

The following cases should always lead to a new style version:

- spelling mistakes were fixed
- A few sentences were rewritten for better readability
- The name of a few variables changed (just the naming and only if it doesn't impact other parts)
- Some styles or colors changed a bit
- Existing texts, strings, buttons etc. were formatted differently
- Details on a design changed

### **Project Stage**

The project stage addition changes whenever the project changes from one stage to another. Every change in that part results in a reset of all previous parts. If the project is still in active development (pre-alpha, alpha, beta, etc.) this addition must be kept, until the first stable production ready release.

There are no specific rules, for when to move from one stage to another. It is recommended to define in advance which features or contents must be present to consider it a new development stage.

For non-coding projects this part might not be relevant, but if used it must follow the same rules,

### **Optional Parameters**

These optional parameters can be anything that makes sense for that project. For further differentiation numbers or letters can be added, separated by a dash or a dot. They still need to follow the basic rule of always increasing and resetting when a higher part is increased. However in which cases these change, can be freely defined. Those rules must be documented in the README.

## **Version Examples**

The following is an example of a versioning history for a component using the CNV. This is not a complete history and just highlights some examples.

| Current Version | Next Version | Changes                                                                                          |
| --------------- | ------------ | ------------------------------------------------------------------------------------------------ |
| v0.1.0.0        | v0.1.0.0     | Work just started on the project                                                                 |
| v0.1.0.0        | v0.1.1.0     | After implementing the most basic inputs, a few bugs needed to be fixed                          |
| v0.1.1.0        | v0.2.0.0     | More logic was added, some other bugs were found and fixed                                       |
| v0.2.3.2        | v0.3.0.0     | Even more logic was added                                                                        |
| v0.3.9.2        | v0.4.0.0     | Yet another functionality change was made, increment leads to overflow to the next major version |
| v0.4.6.8        | v1.0.0.0     | Component is production ready and released for use                                               |
| v1.0.0.0        | v1.0.0.1     | A typo was fixed, nothing else was changed yet                                                   |
| v1.0.0.1        | v1.1.0.0     | A security issue was fixed                                                                       |

Here are some more example of how a version string might look.

| Version String  | Refers to                                                                                               |
| --------------- | ------------------------------------------------------------------------------------------------------- |
| 0.2.4.5         | A non-production ready version, still in early development                                              |
| 0.2.4.5-alpha   | A non-production ready version, in alpha stage                                                          |
| 0.2.4.5.f-alpha | A non-production ready version, in alpha stage, with custom f addition                                  |
| 2.4.0.5         | The second major production ready version, with some additions in functionality and small style changes |
| v2.4.0.5        | Same as previous, just with a prefix                                                                    |
| d2.4.0.5        | Same as previous, just with a different prefix, that could indicate that it belongs to a document       |
| v2.4.0.5-abc    | Production ready release, with additional part, that could indicate numerous things                     |
| v2.4.0.5.a.c    | Production ready release, with two additional parts, that could indicate numerous things                |
