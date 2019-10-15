---
back: "./01-introduction.html"
home: "./"
next: "./03-mymadlib.html"
---

## Unit 4 - Bots - Chapter 2 Implement your bot


### Build it:

Now that you have see the Mad Libs bot in action, let's build it!


1. Log into the [Bot builder website](https://va.ai.dynamics.com) using the account provided to you in class. 
   
2. Once logged in, click the bot icon in the upper right, and then press the new bot button.

    ![New Bot](./img/mlbot01.png)

3. You will now asked to name your bot and tell it what environment it will live in. Let's name our bot "Mad Libs Bot" and put it in the "Developer Environment", and then press the "Create" button. It will take a few minutes for your bot to be created.
   
    > NOTE: that you have to press the options drop down to set the environment. 

    ![Create Bot](./img/mlbot02.png)

4. When the bot is created, there are some sample topics that we need to delete. Select "topics" from the navigation on the left, and then press the "trash can" next to each of the "user topics" to delete them. NOTE: you should not modify the "system topics".

    ![Delete unused topics](./img/mlbot03.png)

5. Now we are ready to create our first topic. The purpose of this topic is to start the "Mad Libs" game. Press the new topic button. Set the title to "Mad Libs Greeting", and the description to "This topic will start the Mad Libs Game". 
   
6. Our topic will need 5 trigger phrases. Add the follwing:
   1. "Start the Game"
   2. "I want to play a game"
   3. "Mad Libs game"
   4. "ml"
   5. "game time"

7. It should look like this, then press the conversation "edit" button

    ![Create greeting topic](./img/mlbot04.png)

    You should now see an empty topic, with your trigger phrases at the top and an empty "Bot Says" box.

    ![Empty greeting topic](./img/mlbot05.png)

8. In the "Bot Says" box, enter the text "What Mad Libs would you like to do?"

9.  Now click "user says" from the bot design surface, and enter "Story 1" as the first option. It should look just like this. 

    ![Story 1 Greeting](./img/mlbot06.png)

    Since we have not created our first Mad Lib yet, we will need to come back here to attach this "users says" to our Mad Lib. 

10. However, Lets add a "fallback" option if our user enters a response that we are not expecting. If you put your mouse over the line connecting the "user responses" to the "users says" you should see a little "plus sign" clicking on it will provide you a menu to add a "fallback"

    ![Greting fallback create](./img/mlbot07.png)

11. In the fallback branch (i.e. the one that says "none of these user responses") add a bot says with the following text "I don't have that one, please try again.". It should look like this. And then save your changes using the button in the upper right. 

    ![Greeting fallback done](./img/mlbot08.png)

12. Now lets, create a new topic our "Mad Libs Close". After our user completes the Mad Libs Game this topic will thank them. Start by clicking "topics" from the menu on the left and then "new topic".

    ![new topic close](./img/mlbot09.png)

13. Enter the Name of this topic "Mad Libs Close" and give it a description "This topic will end the Mad Libs Game". This topic will not have any triggers, so you can press "edit" to sart adding the conversation. 

    ![close topic title](./img/mlbot10.png)

14. The bot will now thank the user for playing and ask them if they want to play again. Add a bot says with the following text "Thank you for playing my game! Would you like to play again?"

15. The user response will be either "Yes" and "No", add these to the bot designer. Your topic should look like this now. 

    ![close topic choice](./img/mlbot11.png)

16. Now lets tell the yes branch to Go to the "Mad Libs Greeting" topic, and tell the no branch to go to the "Goodbye" topic. It should now look like this. And then save your changes using the button in the upper right. 

    ![close topic go to](./img/mlbot12.png)

17. Now that we have created topics for starting and ending our game, lets program our first mad libs game. 

18. Lets create a new topic called Story 1.  Start by clicking "topics" from the menu on the left and then "new topic".

    ![new topic close](./img/mlbot09.png)

19. The title for our topic will be "Story 1" and the description will be "this topic will show the user the first story". Like the close topic, this topic will not have any trigger phrases, so you can just start editing the conversation. 

    ![new topic close](./img/mlbot13.png)

    Rembember that our first story looks like this.
    ![Mad Libs Example](./img/ml01.png)

20. So our bot needs to ask our user for the exclamation value to fill in the first blank. In the Bot Says box enter "Question 1: Tell me an exclamation?".

    ![Question 1](./img/mlbot14.png)

21. Now we need to collect the answer to the first question and store that value in a variable. We do that by adding a "User Says" to the bottom of our conversation. There will be no choices so you need to delete the empty response that is created by default.  

    ![delete empty response](./img/mlbot15.png)

22. Now we can create the variable that will hold the answer. Press the "add variable" button and then "create variable" 

    ![add variable part 1](./img/mlbot16.png)

23. Lets name our variable "Answer1", set its type to "text" and then press "done".

    ![add variable part 2](./img/mlbot17.png)

24. The bot builder will create an "expression" step in the conversation. We don't need it, so press the three little dots on the upper right of the "expression" step and delete it. 

    ![delete expression](./img/mlbot18.png)

    Our conversation should look like this now. 

    ![first q and a](./img/mlbot19.png)

25. We now need to repeat steps 20 - 24 for the next three questions. Use the following values to fill out your conversation. 


    | Question | Bot Says | Variable Name |
    | -------- | -------- | -------------- |
    | 2 | "Question 2: Tell me an adverb?" | Answer2 |
    | 3 | "Question 3: Tell me a noun?" | Answer3 |
    | 4 | "Question 4: Tell me an adjective?" | Answer4 |

    Your topic should now look like this.
 
    ![q and a topic](./img/mlbot20.png)

26. Now we have all the answers stored in variables, we need to put them in our story. Put the following text in a bot says block. "Answer1! he said Answer2 as he jumped into his convertible Answer3 and drove off with his Answer4 wife." 

27. Now double click on "Answer1" in the string you just entered. Then click on the "{x}" button to replace the text with the "Answer1" variable. Repeat the process for the other 3 answers. It should look like this when you are done. 

    ![story](./img/mlbot21.png)

28. Now after we show the story to the user, the user needs to "go to" the "Mad Libs Close" topic. Select, "Go to" from the box at the end of the conversation and then pick "Mad Libs Close". it should now look like this. And then save your changes using the button in the upper right. 

    ![story](./img/mlbot22.png)

29. The last step is to connect our "story 1" topic to the "mad libs Greeting" topic. Click on "topics" on the left, then press the pencil on the "mad libs Greeting" topic. 

    ![update open](./img/mlbot23.png)

30. Find the Users Says, Story 1 block, and add a "go to" for our first story topic. And then save your changes using the button in the upper right. 

    ![go to story](./img/mlbot24.png)

31. Great, now it is time to test out our bot! Click the "test your bot" button in the lower left of the screen.

    ![test your bot button ](./img/mlbot25.png)

32. Next press the "start over with latest content" button, and then enable the tracing switch. 

    ![reset and trace](./img/mlbot26.png)

33. Now you can send any of the trigger phrases to the bot to start playing the game.

    ![trigger the bot](./img/mlbot27.png)

Done!