# Problems Suggestions

Problems Suggestions is the area of the project where the Agents can look for the most common problems that have occurred within the company and how they can be solved.

#

## Few Notes Before Start

This application was divided into various repositories in order to generate the 
functionalities of each area in a more orderly, clean and concise way, as well
as to have order in the code sections that will be presented on this wiki.

#
# Documentation
##  [FrontEnd](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend)

**Brief explanation**:

In this section, the agent can search for problems and solutions by typing them in the search bar of the Problems Suggestions card, the agent can also send a solution suggestion to a question created by an administrator.
The administrator can create a new problem, a new problem category, accept or decline solution proposals and delete questions and/or answers.

**Components**:

In the FrontEnd section, you will find the description and visuals including the problem suggestions card, as well as the solutions proposals display, you will also find the create problem and create category cards.

* [ **QuestionList.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/AgentCards/QuestionList.js)

This component helps us display a list with all the questions of a
specific problem of the problems list.

* [ **ProblemCategoryList.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/AgentCards/ProblemCategoryList.js)

This component helps us display a list with all the
categories of the problem suggestions.

* [ **AnswerList.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/AgentCards/AnswerList.js)

This component serves as a container for all the possible answers that a 
problem has.

* [ **AddSolutionModal.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/AgentCards/AddSolutionModal.js)

It's a popup screen that is triggered by clicking
the add solution button found in the AnswerList component.

* [ **ProposalsList.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/AdminCards/Problem%26Solutions/ProposalsList.js)

Component that fetch all the categories for the proposals card.

* [ **Proposal.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/AdminCards/Problem%26Solutions/Proposal.js)

Represent a proposal of the proposal list in the administrator configuration.
     <ul style="list-style-type:circle">
     Functionalities:
     <li> Delete a proposal
     <li> Approve a proposal
     </ul>

* [ **NewSolution.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/AdminCards/Problem%26Solutions/NewSolution.js)

This component display de card that allows the administrator to add a new solution

* [ **NewProblem.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/AdminCards/Problem%26Solutions/NewProblem.js)

This component display de card that allows the administrator to add a new problem

* [ **NewCategory.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/AdminCards/Problem%26Solutions/NewCategory.js)

This component display de card that allows the administrator to add a new category

* [ **AdminSolutionList.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/AdminCards/Problem%26Solutions/AdminSolutionList.js)

This component display all the approved solutions.
  <ul style="list-style-type:circle">
  Functionalities:
    <li> Change to create solution card.
    <li> Change to proposal card after fetching all the not approval solutions.
    <li> Close this card component.
  </ul>

* [ **AdminSolution.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/AdminCards/Problem%26Solutions/AdminSolution.js)

Displays a solution from the list of solutions and adds edit and delete buttons

* [ **AdminProblemList.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/AdminCards/Problem%26Solutions/AdminProblemList.js)

Component that fetch all the problems for the update problem card.

* [ **AdminProblem.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/AdminCards/Problem%26Solutions/AdminProblem.js)

Represent a Problem of the proposal list in the admin configuration.
  <ul style="list-style-type:circle">
  Functionalities: 
  <li> Change to Solutions Card after fetching all the approved solutions.
  <li> Delete a Problem
  </ul>

* [ **AdminCategory.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/AdminCards/Problem%26Solutions/AdminCategory.js)

Displays a category from the list of categories and adds edit button, this allows the administrator to make 
changes on the solutions of any category

* [ **AdminCategoriesList.js**: ](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-frontend/blob/master/src/components/AdminCards/Problem%26Solutions/AdminCategoriesList.js)

Component that fetch all the problems for the update problem card.

## [BackEnd](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-backend)

**Brief explanation**:
In this section you will find the controller, model and routes for the problem and solution suggestions functionality. 

**Routes**
![image](https://user-images.githubusercontent.com/65176328/174455524-632434a9-89df-4b40-817a-b1eac9a835ac.png)
![image](https://user-images.githubusercontent.com/65176328/174455536-24006555-d7b3-4b76-a2c6-8c0111b57619.png)
![image](https://user-images.githubusercontent.com/65176328/174455542-319deb43-f726-425b-997f-4829ad01d669.png)
![image](https://user-images.githubusercontent.com/65176328/174455550-b01b833e-af2f-4028-8495-9d7f8e36f583.png)

**Models**\
[categoryProblem.ts](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-backend/blob/main/src/models/categoryProblem.ts): Specify the data to store information about the relation between the caregories and the problems. The data needed for this model is:
- problem_id
- category_id  

[problem_category.ts](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-backend/blob/main/src/models/problem_category.ts): Specify the data to store information about the categories. The data needed for this model is:
- category_id
- category_name
- category_description

[problem.ts](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-backend/blob/main/src/models/problem.ts): Specify the data to store information about the problems. The data needed for this model is:
- problem_id
- problem_description
- created
- submitted_by

[solution.ts](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-backend/blob/main/src/models/solution.ts): Specify the data to store information about solutions. The data needed  for this model is:
- solution_id
- solution_description
- approved_date
- created
- problem_id
- submitted_id
- approved_by

**Controller**\
[ProblemCategoryController](https://github.com/AmazonConnect-TECCEM-502/amazonconnect-backend/blob/main/src/controllers/ProblemCategoryController.ts)
