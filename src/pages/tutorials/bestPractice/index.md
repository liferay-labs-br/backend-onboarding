---
title: "Best Programmings Practice"
description: "This section shows some tips and good programming practices, showing how to organize the code and also the meaning of a clean code."
layout: "tips"
icon: ""
weight: 4
---

###### {$page.description}

<article id="1">

## Clean Code

- **Simple:** easy to understand code.
- **Straight:** go straight to the point, do not "loop" to achieve your goal.
- **Efficient:** code that does what is proposed.
- **No duplicity:** it does not do what another part of the code already does.
- **Elegant:** because it is different from other codes.
- **Done with care:** those who did had concern in producing that code.

</article>


<article id="2">

## Programming Practices 

- **Add new methods in alphabetical order relative to the existing code. [JS]**
- **Do not deploy with any running breakpoints.**
- **Check the need to create unit tests before performing the pull request.**
- **Perform unit and integration tests before performing the pull request.**
- **Each line of code can not exceed 80 characters.**
- **Do not perform method chaining:**

    ```javascript
    person.setName("Peter").setAge(21).introduce();
    ```

- **Verify that the branch is updated before committing.**
- **Make sure to write JavaDocs when it needed.**
- **Pay attention to finished your task before start new ones.**

</article>
