# spiceTIME

- Tasks:
    2. make app class
    3. make list class (can be done before 1. and 2. are ready, I could do that)
    4. make hoverButton class
    5. add chili button to list item
- Setup:
    - react classes:
        - App (1 instance: contains the background image and the currently shown list)
            - static html/css for header and full viewport background
            - on click of background page:
                - change text on background page (not currently shown list)
                - render the other list that hasnt been shown before

        - List (2 possible instances (only one is shown): toDoList, completedList)
            - inside its state, List has a value listData
                - ListData is a 2D array matrix, of which each inner array item contains all the info for one list item
                - at specific indexes of the inner array, specific information is represented
                    - e.g.: [uniqueNumber, text, isCompleted, isChili, reminder]
            - renders listItems (a function that uses .map() creates a an array of list items based on all the respective information inside listData)
                - if the list item is empty (e.g. respective inner matrix has no text), an input field with a "add item" button appears on click/on hover
                - inside a non-empty list item:
                    - text
                    - doneButton
                    - hoverButtons (on hover)
                    - chiliButton (if isChili==true)
            - has doneButton:
                - is marked if isCompleted==true
                - onClick/ onChange, a function fires which changes isCompleted to !isCompleted (e.g. setState({ isCompleted: !this.state.listData[i][2]}), if isCompleted would be at index 2 of the the inner array)
                - renders app again to show updated list

        - hoverButton (3 instances: delete, reminder, addChili)
            - displayed on hover inside list item
            - delete:
                - deletes the list item info from the listData matrix
                - renders app again to show updated list
            - reminder
                - shows dropdown/ popup where reminder time can be set
                - adds reminder to the item which is shown in the list item
                - renders app again to show updated list
            - addChili
                - sets isChili of respective list item to true
                - list item adds chili icon on right, if isChili==true
        - Chili button (deletes itself on click)