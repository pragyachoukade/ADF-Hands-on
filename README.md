# Azure Data Factory Implementation with Sales Data

This project involves hands-on experience with Azure Data Factory, utilizing sales data to demonstrate various functionalities. The following steps outline the process undertaken:

1. **Resource Group Creation**: A resource group was established to organize and manage various resources effectively.

2. **Storage Account Setup**: A storage account with a hierarchical namespace was created to facilitate the development of a data lake.
![Screenshot (288)](https://github.com/user-attachments/assets/bbeaeb2a-4f06-4d5c-a258-fd510d0adc40)

3. **Azure Data Factory Resource Creation**: An Azure Data Factory resource was set up to enable the creation of pipelines for data loading. To connect with GitHub data, a linked service was established.

4. **Pipeline Development**: A pipeline was created, incorporating a copy activity to transfer data from the GitHub source to the designated destination. This involved creating two containers within the data lake, named "source" and "destination."
![Screenshot (286)](https://github.com/user-attachments/assets/a135d8aa-23f3-4025-a433-cd4388da3bf2)

5. **Scenario-Based Practice**: Two files were stored in one container: a Fact file utilized by the reporting team and another file for the data science team. To enhance security, it was necessary to restrict visibility of the Fact file to the reporting team only.
    a. A separate pipeline was created, incorporating a "Get Metadata" activity to retrieve metadata for the entire folder, which includes all file names. An "If Condition" activity was then applied to filter the files, allowing only those starting with "Fact" to be processed.
    b. **Reporting Container Creation**: A dedicated container named "reporting" was established within the data lake for the reporting team. Only files beginning with "Fact" (e.g., Fact1, Fact2, Fact3) were transferred to this container.
     ![Screenshot (287)](https://github.com/user-attachments/assets/d3ce5e27-408e-4b20-b124-3324ede6875f)

    c. **ForEach Activity Implementation**: A "ForEach" activity was utilized to iterate over the output of the "Get Metadata" activity, facilitating the copying of Fact files to the reporting container.
     ![Screenshot (284)](https://github.com/user-attachments/assets/27ce0685-e28a-494a-8325-e551b012d9c6)

    d. **Data Flow Design**: Data flows, which allow for visually designed data transformations within Azure Data Factory, were employed. Transformations such as column selection, filtering, and aggregation were applied.
![Screenshot (285)](https://github.com/user-attachments/assets/e5536c17-54f2-41ab-99d1-c662749d8ef5)

6. **Pipeline Automation**: To automate the execution of the pipeline, a scheduled trigger was implemented. This trigger ensures that the pipeline runs at specified intervals, executing all activities automatically. The transformed files can be found in the designated folder.
