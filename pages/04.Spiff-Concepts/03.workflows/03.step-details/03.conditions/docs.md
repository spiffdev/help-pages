---
title: Conditions
media_order: 'Screen Shot 2021-06-15 at 9.48.19 am.png,Screen Shot 2021-06-15 at 9.50.12 am.png,Screen Shot 2021-06-15 at 9.52.22 am.png,Screen Shot 2021-06-15 at 10.42.59 am.png'
---

## Conditions

Conditions allow you to **show additional steps** in your workflow **depending** on the **user's selection** for an **earlier step**. 
They are set in the actual step you want to appear conditionally. 

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/03.workflows/03.step-details/03.conditions/Screen%20Shot%202021-06-15%20at%209.50.12%20am.png)

### **How To Use**

1. Create your steps 
2. Go to a step you want to appear condtionally
3. Toggle enable conditions (bottom of step form) 
4. Select the step you are referencing (reference step)
5. Select the variant/asset the user needs to select to show the step (expected variant)
6. Add as many varients as you require
7. Save workflow

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/03.workflows/03.step-details/03.conditions/Screen%20Shot%202021-06-15%20at%209.48.19%20am.png)

Commonly used to offer extra personalisation options. You set a question step with a YES/NO answer to the extra you want to offer. Then you create a step with the extra personalisation component and set it to only render if the user selects YES to the question step.

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/03.workflows/03.step-details/03.conditions/Screen%20Shot%202021-06-15%20at%209.52.22%20am.png)

### Example

An example of conditions in use is on this knife workflow. At the start of the workflow a [question](https://help.spiff.com.au/spiff-concepts/step-types/add-question) is asked if they want to customize the knifes together or seperare. Depending what the user chooses, all steps that follow are conditional depending on their choice.

