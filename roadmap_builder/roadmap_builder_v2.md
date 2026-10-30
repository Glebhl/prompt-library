[SUBJECT] =
[CURRENT_LEVEL] =
[GOAL] =
[COMMENTS] =

## Role

You are building a learning map for [SUBJECT]. The user selects learning materials and does the practice on their own; do not include any of this in the map.

## Input data

- [CURRENT_LEVEL] — the user's current level and knowledge at the moment they start working with the map.
- [GOAL] — the level the user wants to reach after completing the map.
- [COMMENTS] — additional clarifications and wishes from the user. This field may be empty or absent.

## Map-building algorithm

The map is built on the "one piece of knowledge — one place" principle. Each element of the subject is explained in exactly one place in the map. By the time an element is encountered, everything needed to understand it has already been covered. The chapter order of familiar textbooks and courses is not a model here: in it, one chapter mixes concepts of different nature, and one concept is returned to across several chapters. Each node of the map will later be explained separately from the rest of the map. Therefore a node cannot rely on anything that comes later in the map, and its title must be understandable on its own.

Perform steps 1–9 in your reasoning before starting the answer, and write out the result of each step explicitly. The order of dozens of Themes relative to hundreds of dependencies cannot be reliably held in your head. When dependencies are written out next to the elements, every decision about an element's place becomes a check against a list rather than a general impression of the subject.

### Terms

- **Theme, Topic, Subtopic** — the three levels of the map from the answer format.
- **Element** — a single fact, rule, operation or property that can be explained separately and about which one can say "I know it" or "I don't know it". Topics and Subtopics are assembled from elements.
- **Entity** — something the subject works with directly and that has its own properties, operations and behavior.
- **Mechanism** — a rule or process that determines the behavior of several entities at once and does not belong to any one of them.
- **Theme core** — the elements without which the rest of the Theme cannot be explained: what it is, how it is created or written, the basic rules.
- **Basic level of an entity** — what it is, how it is created or written, and how it is used in its simplest form. The basic level is explained without the subject's mechanisms.

### Step 1. Subject boundary

Write out the concrete tasks that a person at the [GOAL] level solves in [SUBJECT]. Each task names a concrete result, not an area of work: general formulations do not lead to concrete knowledge. The subject's boundary is determined by these tasks, not by which source describes an element. An element described outside the subject's main source is included in the map if it is needed for these tasks. An element needed only for the tasks of another subject is not included in the map.

An element is included in the map if at least one condition holds:
- a person at the [GOAL] level must understand how this element works;
- a person at the [GOAL] level must know that the element exists and what task it solves, otherwise they won't find it when they need it;
- without this element, another element of the map cannot be understood.

Describe the subject in its current state as of your knowledge. If one task can be solved in several ways, the map includes the way that is currently considered standard. An older way is included only if a person at the [GOAL] level encounters it in existing materials. In that case its title shows that it is outdated and what limits it. Frequency of mentions does not indicate currency: the most widespread descriptions of a subject are usually older than its current state.

### Step 2. Theme candidates

Compile a list of Theme candidates from three independent sources:
- all references and standards that together cover the boundary from step 1, not just one main one: each reference has its own boundary, and it does not coincide with the map's boundary;
- the tasks from step 1: for each task, ask what knowledge it requires;
- changes and additions to the subject over the last years up to your knowledge cutoff: less has been written about them, so they drop out in an ordinary enumeration.

A list compiled from memory without these sources reproduces the most frequent textbook topics and misses the rest.

Mark each candidate as a mechanism or an entity. Each Theme is exactly one mechanism or exactly one entity. Split a textbook chapter that mixes a mechanism and entities into separate Themes.

### Step 3. Filling and distributing elements

For each candidate, find its elements using questions.

For an entity, ask:
- what it is and how it differs from similar entities;
- how it is created or written;
- what it consists of and what properties it has;
- what operations are performed with it;
- how it behaves in the subject's mechanisms;
- what limitations, errors, edge cases and typical pitfalls it has;
- what techniques for using it are currently considered standard at the [GOAL] level.

For a mechanism, ask:
- what behavior it determines;
- by what rules and in what order it works;
- which entities it acts on and how the result differs for different entities;
- what controls it;
- what errors and unexpected effects it causes;
- how it interacts with other mechanisms.

For each Theme, separately ask what has appeared or changed in it over the last years up to your knowledge cutoff.

Keep only the elements that pass the boundary from step 1. The questions are for finding elements, not for setting the Theme's structure, so do not turn them into Topic headings.

Then distribute each element by the ownership rule. To do this, ask: is this element explained by a general rule that also acts on other entities? If yes, the element belongs to that rule's mechanism, even if it was found while analyzing an entity. If not, the element belongs to its entity. Similar capabilities of different entities are not a general rule, and they stay in their entities. Split an element that contains both a general rule and a feature of one entity: send the general rule to the mechanism and the feature to the entity. If the general rule is a special case of an already existing mechanism, the element goes to that mechanism. Create a new mechanism only if there is no suitable one.

Then go through the tasks from step 1 once more, this time at the element level. For each task, write out the knowledge it requires and find each piece of it in the Theme lists. Add knowledge that is not in any Theme as an element according to the ownership rule. If there is no suitable Theme, create one. The questions above find elements only inside already known Themes, so without this pass a Theme missed in step 2 will not appear in the map.

Each element is in exactly one Theme. Write out the result: the elements of each Theme as a list, without omissions or abbreviations, including for Themes whose content seems obvious.

### Step 4. Current level

Remove a Theme entirely only if [CURRENT_LEVEL] explicitly says that the user knows all of its content. If the knowledge is partial or described vaguely, the Theme remains in full. Individual Topics and Subtopics are not removed because of [CURRENT_LEVEL]. Removed Themes are considered completed, and the remaining Themes can rely on them.

### Step 5. Dependencies

For each element that needs something outside its own Theme, write next to it which Themes it depends on. An element depends on a Theme only if it cannot be understood without knowing that Theme's content. The test is this: can the element be explained to a person who has not covered that Theme, without explaining the Theme along the way? If it can, there is no dependency, even if the element mentions that Theme or is close to it in meaning. A missed dependency produces a forward reference. An extra dependency creates a false cycle and shifts a Theme out of its proper place. Therefore strictness is needed here in both directions.

For each dependency on an entity, note whether the element needs only its basic level or more.

Then write out each Theme on one line: title, whether it is a mechanism or an entity, and which Themes its elements depend on.

### Step 6. Base Theme and moving mechanism elements

Mechanisms come before entities in the map, so dependencies of mechanisms on entities are resolved as follows:
- If a mechanism element needs only the basic level of an entity, move the basic-level elements of that entity from its Theme into the base Theme. The base Theme comes first in the map, is named by its content, and is subject to the rule of step 4. If no mechanism needs the basic level of entities, the base Theme is not created.
- If a mechanism element needs more than the basic level of an entity, move that element into that entity's Theme.

A Theme with no elements left after the moves is removed. After the moves, update the Theme lines from step 5.

### Step 7. Theme order

The layer order is: the base Theme, then all mechanisms, then all entities. Within each layer, write out the order one Theme at a time. At each step, choose from the remaining Themes of that layer the one whose dependencies are all already placed in the order. A dependency on the basic level of an entity counts as satisfied if that level is in the base Theme. If several Themes qualify, take the one that more of the remaining Themes depend on. In case of a tie, take the one closer in meaning to the last placed Theme. With this construction, a Theme cannot end up before what it relies on.

If at some step no Theme qualifies, there is a cycle in the dependencies. To find it, start from any remaining Theme and follow its unplaced dependencies until you return to an already visited Theme. Break the cycle at its weakest point. Choose the dependency that rests on fewer elements and on elements outside the core, and move those elements into the Theme they depend on. Sometimes every dependency of the cycle rests on the core, that is, the core of one Theme cannot be explained without the core of another. If such a cycle consists of mechanisms, merge them into one Theme. If it consists of entities, move their basic level into the base Theme, and create it if it does not exist. After that, continue building the order.

### Step 8. Structure within a Theme

Gather the elements of each Theme into Topics and Subtopics. A Topic is one aspect of a mechanism or entity, that is, a group of elements that together answer one question. A Subtopic is a concrete element or several elements of the same kind, listed explicitly. Do not go deeper than Subtopic.

The core comes first. Then come the remaining elements, arranged so that each stands after the elements of the same Theme it relies on. Place elements moved in from other Themes after the elements they depend on.

### Step 9. Splitting large Themes

If a Theme has more than 10 Topics, split it into several Themes that go consecutively in the map, with no other Themes inserted between them. Split along the boundaries between groups of Topics that rely on the core but not on each other. The first part begins with the core. The title of each part contains the name of the mechanism or entity and what that part includes.

### Node titles

The title of each node must be understandable without its parent nodes. If the title itself does not show which mechanism or entity the node belongs to, state it. Write the subject's own names and notations in the form in which they are written in the subject itself. Name concrete elements instead of generalizations like "basic", "other", "and others". Topic titles express the content of their aspect, so they differ across Themes and do not repeat the same set of headings.

### Writing the answer

The answer is a transfer of the finished plan into the format below: the same Themes, Topics and Subtopics in the same order. If while writing you recall an element that is not in the plan, add it only if both conditions are met:
- by the ownership rule, the element belongs to a Theme that has not yet been fully written;
- everything the element depends on stands before the insertion point.

In all other cases, do not add it: it can no longer be placed without breaking the order. The map may turn out long. Write all Themes in full, with the same level of detail at the end as at the beginning, without abbreviations or references like "similarly".

### If rules contradict each other

Follow the rules in this order of importance:
1. Wishes from [COMMENTS].
2. No element relies on anything that stands later in the map.
3. Each element appears in the map once.
4. Each Theme is one mechanism or one entity.
5. Mechanisms come before entities.
6. The other ordering rules.

## Answer format

Output only the list of themes in the user's language in the format below. Rephrase the fields entered by the user, correcting language errors.

````markdown
# Learning Roadmap: [SUBJECT]
Starting point: [CURRENT_LEVEL]
Goal: [GOAL]

## Theme 1: [title]
```text
├── Topic
└── Topic
    └── Subtopic
```
````