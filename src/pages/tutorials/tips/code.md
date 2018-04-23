---
title: "Code"
description: ""
layout: "tips"
icon: ""
weight: 1
---

###### {$page.description}

<article id="1">

## New Code?

1. On the terminal, access the modified code folder and run the command:
```
'gw clean deploy'
```

</article>

<article id="2">

## Do you want to organize your code before Pull Request?

1. In the terminal, run the following commands:
    - Check for inconsistencies.:
    ```
    'gw formatSource'
    ```
    - Check for inconsistencies in the .jsp file:
     ```
    'check_sf **/*.jsp'
    ```
    - check for inconsistencies in the .soy file:
     ```
    'mcritic XXX.soy'
    ```

- To run the command 'mcritic XXX.soy' command, you must perform the following:
    1. In the terminal:
     ```
    'npm install -g metal-soy-critic'
    ```
    2. Any questions, access [metal-soy-critic](github.com/metal/metal-soy-critic).

- To run the command  'check_sf **/*.jsp', you must perform the following:
    1. In the terminal:
     ```
    'sudo npm install -g check-source-formatting' 
    ```
    2. Any questions, access github.com/natecavanaugh.

</article>


<article id="3">

## Do you want to run tests?
 
1. In the terminal, access the test file of the folder containing the modified code.
2. Unit tests: 
    ```
    'gw test'
    ```
3. Integration Tests:
    ```
    'gw testIntegration'
    ```

    - Something's Wrong ?
        1. In the terminal, run the command:
            ```
            'telnet localhost 11311'
            ```
        2. Check to see if the test file has been installed and uninstalled.
            ```
            'uninstall _NUMBER_FILE'
            ```
            - Observe the test file number and replace in 'XXX'
            - To quit telnet: control + ']' .
        3. **Repeat the tests!**


</article>

<article id="4">

## Run the command 'Ant all'
1. Drop the server.
2. Access the life-portal.
3. Git clean -fdx.
4. Git pull upstream master.
5. Git push origin master.
6. Run the command: 'Ant all'.

</article>


<article id="5">

</article>