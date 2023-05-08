Reasons to change software:
	- Adding a feature
		○ Adding code -> adding behavior
	- Fixing a bug
		○ Modifying code -> changing behavior
	- Improving the design
		○ Refactoring -> Alter the structure of the code but keep the behavior intact
	- Optimizing resource usage
		○ Alter the performance but keep the behavior

|                | add feature | fix bug | refactor | optimize |
| -------------- | ----------- | ------- | -------- | -------- |
| structure      | x           | x       | x        |          |
| functionality  | x           | x       |          |          |
| resource usage |             |         |          | x        | 

Big challenge: Preserving behavior when adding or modifying code

Mitigate risk by asking yourself these question:
	- What changes do we have to make?
	- How will we know if we have done them correctly?
	- How will we know that we have not broken anything?
