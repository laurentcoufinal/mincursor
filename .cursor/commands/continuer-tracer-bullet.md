# continuer-tracer-bullet
For each feature listed in CDC{project}.md:
- If the feature status is "reserved", locate the corresponding file named
todolist-{project}-{feature}.md and proceed to complete all remaining unfinished
steps in that file before continuing to the next feature :
- For existing presentation and data access layers (files, databases, or
services), do not rewrite code; instead, generalize the integration where possible
and use interface patterns if needed.
- For all business logic related to a feature, develop it within a dedicated
/{feature} directory.
- For each function, first write unit tests to achieve at least 60% test
coverage. Then, implement the function. Run the tests, fix any failing cases if
necessary, and only then proceed to the next function.
- After completing each step (UI, business logic, database access, file access,
etc.) and after each integration phase, run the tests. If they pass, ask me for
validation before continuing; if not, correct up to three times. If the tests still
do not pass after three attempts, stop and ask me how to proceed.
- Follow all applicable rules.
- only mark steps as validated after I confirm them.
- If the feature is not reserved, take the CDC{project}.md and fully implement
the remaining features that are neither done nor reserved, one by one, end-to-end
until each is functional :
- Before starting, mark the selected feature as reserved in CDC{project}.md.
- Plan each step carefully: design, development, unit testing, integration
testing, and acceptance.
- Choose the execution order to make integration testing easier.
- Write acceptance tests before you write code, which we'll use to validate the
implemenation.
- Generate behavior-driven development scenarios in given-when-then format that
trace directly back to your users stories and acceptance criteria.
- Create test datasets that systematically exercise boundary conditions, edge
cases, and error scenarios
- Generate comprehensive regression test suites whenever you modify existing
functionality.
- For existing presentation and data access layers (files, databases, or
services), do not rewrite code; instead, generalize the integration where possible
and use interface patterns if needed.
- For all business logic related to a feature, develop it within a dedicated
/{feature} directory.
- For each function, first write unit tests to achieve at least 60% test
coverage. Then, implement the function. Run the tests, fix any failing cases if
necessary, and only then proceed to the next function.
- After completing each step (UI, business logic, database access, file access,
etc.) and after each integration phase, run the tests. If they pass, ask me for
validation before continuing; if not, correct up to three times. If the tests still
do not pass after three attempts, stop and ask me how to proceed.
- Follow all applicable rules.
- Record all steps in a file named todolist-{project}-{feature}.md, and only
mark steps as validated after I confirm them.
