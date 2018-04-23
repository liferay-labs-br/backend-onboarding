---
title: "Routine"
description: "The backend team routine consists of daily work combined with strategic management to achieve the expected results. This strategic management is based in effective meetings, balanced workload and collaborative team spirit. This section will describe the ticket management and all meetings."
layout: "team"
icon: "calendar"
weight: 5
---

###### {$page.description}

<article id="1">

## Ticket Management

All the work in progress in engineering is monitored by a issue management (Jira). This system provides bug tracking, issue tracking, and project management functions. In other words, helps the team to keep an eye on all the activities day by day.
Every team has your own kanban board with all your integrants as participants. In that way, Everyone knows which activity is aimed at who and their progress throughout the sprint. The image below shows a kanban board, which it can be noticed the participants and their issues. 

<img src="/images/kanbanBoard.png" />

This image below shows one created ticket:

<img src="/images/bugIssue.png" />

There are 5 types of work:
- **Story:**  Small unit of work to deliver a particular value back to the customer. 
- **Bug:** An error in a system that causes it to produce an incorrect or unexpected result.
- **Regression bug:** Regression is when something that used to work fine does not work properly anymore.
- **Task:** Reflect work or initiatives that are very technical.
- **Pull Request:** Reviews from different teams and components.

Every work has a different workflow from the creation of the ticket until the delivery of the expected result. This example below shows the step by step and the workflow to a new user story:
1. **Open:** Product Manager or Technical Leader create the user story.
2. **Backlog:** Product Designer development.
3. **Ready for development:** List of stories ready to be developed.
4. **Selected for development:** List of stories committed to be developed in the next 2 weeks.
5. **In Development:** Engineers start working on the story.
6. **In Review:** Once development is completed, peer review, QA review and validation and, Brian’s review.
7. **Documentation:** Does the story need documentation? Generate a draft!
8. **Design Review:** Product Designer make sure that the story requirements were developed according to the guidelines provided.
9. **PM Review:** Product Manager validates the use cases.
10. **Closed.**

<img src="/images/userStoryWF.png" />

Bugs are the type of work that needs to be under control, it means that should not exceed a certain limited number. To guide the team which bug they should resolve first, there is a classification based on the [portal risk matrix](https://docs.google.com/spreadsheets/d/1QQn7In1KPTaEe_gy95EoF-ELl0TvBHBaNWqwTV2SxNY/edit#gid=5) that classifies the bug on a scale of 1-5. The developers should resolved the bugs in the descending order of their fix priority.

This image below shows the successful ticket management to the bugs and regressions bugs workflow:

<img src="/images/bugWF.png" />


</article>

<article id="2"> 

## Meetings

The team meetings have the objective to verify the status of the work, but also to check if there is any need or trouble. For a meeting to be productive, it is necessary to list the different motives to be discussed and to mark different sessions to discuss each topic separately. In this way, the meeting does not become exhaustive or confusing.

There are differents types of meetings:
- **Backlog Refinement:** An event to refine and update the backlog with initial effort for each ticket and an opportunity to alignment and re-evaluate tickets and priorities. This meeting will occur every two weeks, in the week before the Planning meeting. It must involve the product manager, technical leader, product designer.
    - every two weeks, in the week before planning meeting.
- **Planning:** Understand the stories with the proper acceptance criteria. The Product Manager will present all the stories for the new cycle and the team will assess each story, commit/accepted it to the sprint and breakdown it into small subtasks.
    - every Monday, check the calendar to see the schedule.
- **Stand Up:** An event for the development team to synchronize activities.
    - daily at 2pm.
- **Product Sync-up:** An event to share and evolve the product collaboratively.
    - Whenever there is a need.
- **Retrospective:** An opportunity for the team to inspect itself and create a plan for improvements to be done during the next iteration.
    - Every two weeks.
- **Guild Reunion:** An event to talk about general topics of the backend as a team or to discuss about a new technology. It is a open space to share any interesting points of view and to suggest any kind of improvements.
    - Every tuesday at 10am.

</article>
 


