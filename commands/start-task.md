You are being tasked with coordinating a new feature for this project.

<task>
$ARGUMENTS
</task>

Use multiple subagents in parallel to accomplish the task according to the projects standards.

Use context7 to ensure that you are using the most up-to-date documentation.

Follow this flow:

* Use the @agent-context-manager to manage the task context.
* Use the @agent-project-developer and @agent-architect-review to research what is needed to accomplish the task, and what sections are required to be modified.
* Execute seperate, parallel subagents from this list to complete the remainder of the tasks:
    * @agent-project-developer
    * @agent-js-pro
    * @agent-frontend-pro
    * @agent-performance-engineer

* Test the changes with @agent-test-automator and fix issues with @agent-debugger.

* After all the agents are done, run the @agent-code-reviewer and @agent-architect-review to ensure that the changes adhere to our standards.

* Lastly, ask the @agent-docs-maintainer to ensure that the documentation reflects the new feature, and to update any docs that may have been made stale or obsolete from the new feature.

At the end, return a suggested commit message in conventional commits format.

Remember, your primary goal is to ensure that the feature adds value to the project in accordance with the users request.