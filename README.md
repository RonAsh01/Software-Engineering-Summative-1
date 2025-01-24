# Software Engineering Summative 1

### Proposing a new project

One idea I had that for a simple web app, or interactive data product, that would work as a new project was a interactive data product that could pull weather related data from a third-party API source, and generate a suite of visualisations displaying this data that could be presented back to the user. This would also include managing a user input, so that the visualisations are specific to the users desired location and time frame.

This project would have a couple of key uses within my organisation workplace, as accurate weather data can be difficult to ascertain. One key use could be to assess weather forecasts at alternate or diversion airports, prior to, or during, flight, as opposed to much closer to landing. This would also drive additional sustainability benefits, as it would allow for an assessment of whether the alternate airports being selected and filed for a flight are the most appropriate options, or whether there are other alternatives, with an acceptable weather forecast, that are closer. If this were the case, benefits could be derived from lower fuel costs, as less would have to be loaded initially, and less used in the case of a diversion. 

### Prototyping

Prototyping is the process of developing a mock-up of a project solution or deliverable, with the main aim of gaining feedback from the stakeholders, regarding user experience and features. Prototypes are very rarely fully functional products, instead serve as a base for visual and interactive development. 

Before beginning the development of a product prototype, it is useful to consider the agreed scope of the project, and what requirements will need to be developed, and hence go into the prototype, to meet this scope. Below is a realistic list of requirements for a project of this scope:
User Experience:
Input field for airport/aerodrome.
Input field for date/number of forward forecasting days.
A button to run the process.
Easy-to-understand visualisations to present the data to the user.
Data:
Live data sourced from an API.
Wide range of locations available.
User input validation & error checking:
Validation checks for user-inputted fields, and a simple error message to aid the user should the process fail due to this.
Simple error messages should any other part of the process fail.

Once these requirements had been defined and I was confident that they satisfied the scope of the project, I could begin to develop the prototype using Figma. This is a software that allows one to create a prototype that includes visual and interactive elements that is then used to present to the stakeholders to gain feedback and insights from what the stakeholders desire, in order to ensure that project development is on the right track from the offset.

The prototype that I developed included a launch page, that showcased the user input that would be required to generate the relevant visualisations using the API, as well as the interactive buttons that would allow the user to navigate between the different pages. The actions that these perform can be seen below in Figure 1, and are shown by the blue lines that connect   I also included a mock-up to show what the graphs would roughly look like, although, being a prototype, these graphs are static and just for demonstration purposes.


Figure 1: Figma prototype, including the interactive flow.

### Planning & Project Management

Planning and project management is a key part of software development. It is the use of specific knowledge, tools and skills to work through the phases of a project life cycle towards a defined deliverable. There are several different approaches that can be taken for project management, each taking slightly different approaches and utilising different methodologies to manage and track the progress of the project. For the development and management of this project I opted to take a more agile approach, using a kanban board with swim lanes to track the project workflow. An agile approach is much less linear than a traditional waterfall approach, and instead involves breaking down the project development timeframe into much smaller, more iterative periods, often called ‘sprints’ or ‘scrums’. Additionally, this more incremental approach means more work can be developed simultaneously, instead of the more limited linear approach that is associated with a waterfall methodology. The agile methodology that I opted to use was Kanban. This involved using a kanban board with swimlanes that track project workflow. The required work is broken down into several smaller tasks that progress along 

For my project, I adopted the kanban methodology, but opted not to utilise the full agile approach, as I didn’t believe it would bring any considerable benefits considering the scope, short timeframe and small number of personnel involved in the work. My Kanban board consisted of five swimlanes, using the following titles:
To-do - Tasks for which the applicable work has not yet been commenced.
Blocked - Tasks where the applicable work has commenced, but has been blocked by something that requires external input, i.e. data systems access.
In Progress - Tasks where the work is currently underway and progressing
User Acceptance Testing (UAT) - Tasks which have been completed and the business stakeholder updated, but there may be some feedback to action.
Done - Tasks which have been completed.

Despite being a sole developer on this project, I found that the Kanban board and methodology still aided me in keeping track of outstanding work and tasks, and allowed me to more effectively evaluate my workload which, in turn, helped with planning my work schedule, as I could better understand the quantity of work I had outstanding on this project. This is made even more simple by using the agile principle of story points, where each task should be worth 1 story point, or about 1 days worth of work. Again, due to the smaller scale of this project I was unable to utilise higher-level agile features, such as epics and stories and the higher story points that would be associated with those features.


Figure 2: Image of the Kanban board I used to track project tasks.

### MVP Development & Documentation

Having created a prototype that met the criteria for the project deliverable, I could begin to work on actually developing a Minimum Viable Product (MVP) that closely replicated the prototype and could be delivered to the project stakeholders. An MVP does not necessarily always represent the final project deliverable, but is functional product that meets the original basic product expectations and can be reliably used by stakeholders in their day-to-day work. 

The majority of the code behind the MVP I developed is modular, as this facilitated a simpler development process. This involved developing a series of functions, each corresponding to a specific part of the process of sourcing, processing and visualising the data from the API, such as fetching, processing and storing daily and hourly data from the API, and generating the visualisations. 
The functions that load, process and store the data returned from the API use dataframes to store the data in, as these are generally the simplest to then build visualisations from. However, because the API data begins in json format there are couple of steps that thata re undertaken to transform this into a dataframe. Firstly, there is a dictionary which aids in accessing the correct part of the API’s json response, and an empty list that data will be temporarily stored in. The functions then use a for loop to loop through each day, and hour if applicable, and append the specified data into the list. This list is then returned as a dataframe when the function is later called upon.

One benefit of having a modular code design, particularly during development, is that it makes developing similar sections of code more efficient, such as the sections in my code that process daily and hourly data - as these are two very similar tasks I was able to develop successful code for one of these tasks, and then just duplicate and adjust it for the other. This makes the code development process more efficient and also less error-prone, as I had the assurance of using already successful and tested code.

Additionally, there is also a couple of benefits when it comes to error handling, as it is easier to identify and locate the code source causing the error. Firstly, this is beneficial from a development point-of-view, as erroneous code can be identified quicker and, hence, corrected quicker which contributes towards a more efficient development process. The second error handling benefit concerns the user experience. The modular code setup should enhance the user experience, as being able to identify which section, or function, of the code has failed should allow a more concise error to be shown to the user, which may be able to aid them in understanding and correcting the error. One example of where this is built into the code is during the API connection and data fetching function, which can be seen below in Figure 3. 


Figure 3: Error handling with a try except block.

Error handling such as this is also present for the interactive sections of the app, where the user is prompted to enter information such as location and quantity of forecast days. In this instance, it does some basic checking to ensure the location and number of days entered is valid, and returns a pop-up error message if not.

The MVP product I have developed uses Matplotlib and Seaborn to generate the visualiastions and Tkinter to provide the Graphical User Interface (GUI) that the user interacts with. The two aforementioned visualisation tools are simple to work with, and provide good customisation options, such as the functionality to change colours and add legends and reference lines for fixed values. Tkinter has allowed me to develop the front-end GUI that the user experiences when running the product, and also is fairly simple  and practical to use. It also has the functionality, when combined with Matplotlib, to embed the visualisations into the GUI, instead of them just appearing in the Jupyter Notebook. This adds to create a cleaner and simpler to use interface for the user.

In order to run the data product in the notebook, one must first ensure that Jupyter Notebook is installed on the system they are attempting to run the product one - if the system is running on company equipment then this requirement should already be satisfied. The product can be run on several programmes, e.g. Jupyter Notebook itself, or a code editor such as VSCode. However, regardless of the programme being used to run the product, Jupyter Notebook must first be launched from the command line. This will open the notebook dashboard, which, if one desires to run the product through Jupyter Notebook itself, is where the path to the .ipynb file can be located, loaded and run. If the user desires to run the product through another code editor, this has to be launched and connected to the running Jupyter server - this is the link in the command line that begins “http://localhost:8888/” . When attempting to run the notebook file in an editor such as VSCode, it will prompt the user to enter this link, so that the editor can connect to the Jupyter server and run the notebook.

#### Test Driven Development

Test driven development is the process of building code by writing tests before writing the code that these tests are applicable to. This ensures that the code tested is not only always functional, but also as minimal and concise as possible. This could be integrated into the modular code design I have used, to develop the code for each function as efficiency as possible.

### Future Scope & Development

Being an MVP and not a final project deliverable, it means there is still scope for further development. One non-critical change I would like to make is in regards to the design of the visualisations. Although the visuals are functional, and include a colour blind friendly colour scheme, they are not the most impressive, and some additional visual enhancements could improve the GUI. I would also like to include the addition of some historical data, whether that is also sourced from an API or just stored locally within the code from previous run instances, as this could increase the scope in which this product is usable and applicable.

Additional testing for accessibility and performance could also be a future point of development, or area that I would change should I ever undertake a similar project, although, being an MVP, some of this can be worked out with the stakeholders in the near future.

### Evaluation

Overall, I think that the MVP I have developed and delivered successfully meets the original project scope and demands, and should provide value to the business area and applicable stakeholders.
