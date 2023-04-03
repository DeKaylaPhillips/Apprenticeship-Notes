# SOLID OBJECT-ORIENTED DESIGN by SANDI METZ

Resource - https://www.youtube.com/watch?v=v-2yFMzxqwU

- In OOP, the SOLID principles are a set of guidelines that help developers to write software that is easy to MAINTAIN and EXTEND over time.

    >   Open-Closed Principle (OCP), states that software entities (classes, modules, functions, etc...) should be open for extension but closed for modification.
    >   When you need to add new functionality to an existing system, you should do it by adding new code rather than modifying existing code.

- Allows you to avoid introducing bugs of unintended consequences into the system by accidentally changing something that is already working as expected.

**Rigid Applications:**

- everything is connected to everything else
- every change causes a cascade of changes
- does not follow the OCP principle and is difficult to extend without making modifications to the existing code
- makes it harder to maintain and evolve the software over time
- every change to the system requires modifications to existing code that can introduce new bugs or unintended consequences

i.e.) Suppose you have a class that represents a shape and has a method to calculate its area. If you want to add support for calculating the perimeter of the shape, a rigid application would require you to modify the existing shape class to add the new functionality.

- This violates the OCP principle, as modifying the existing code may introduce new bugs or unintended consequences.

**Fragile Applications:**

- fragile apps are rigid, but you can't tell by looking at them
- distant and apparently unrelated code breaks after every change

**Immobile Applications:**

- quality where you'd like to reuse some code somewhere else, but you can't extricate it from where it is
- reuse through duplication is required
- code is hopelessly entangled; you can't reuse anything

**Viscous Applications:**

- when you want to make a change, and can tell how the original designer wanted you to behave, but it is easier to do the wrong thing
- behaving badly is the most attractive alternative
