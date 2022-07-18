# Heaps 2D Tutorial (Extension)

- This is the tutorial game with an object oriented design proposal.
  - Every *game piece* (like in a board game) `extends` a common class (here named `GameObject`, it's also common to use "entity" as a name)
  - This makes single files smaller again and may be easier to scale, however using only one class stuffed with functions like before works as well and the approach designed here is only a possible option amongst many others. Another option is data oriented design, for instance with an ECS (entity-component-system architecture).

