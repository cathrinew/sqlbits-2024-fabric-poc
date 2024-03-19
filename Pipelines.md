# Pipelines

As of March 19th, 2023, it is not possible to import pipelines to Fabric 😔 So, we will create them ourselves! We will create the following pipelines:

![Pipelines](/Images/Pipelines.png)

Let's start with the setup first!

## 99_Setup

This Pipeline runs the Notebooks that creates our schemas:

![Pipelines](/Images/99_Setup.png)

Point each Notebook activity to its corresponding Notebook:

![Pipelines](/Images/99_Setup_02.png)

- 99_Setup_Schemas_Bronze
- 99_Setup_Schemas_Silver
- 99_Setup_Schemas_Gold
- 99_Setup_Load_Date_Tables

▶️ Save and run the **99_Setup** pipeline!

✅ Validate that you have all the tables in the Silver_Airbnb and Gold_Airbnb lakehouses.

## 10_Bronze

This Pipeline runs the sub-Pipelines that ingests our data:

![Pipelines](/Images/10_Bronze.png)

This may seem superfluous at this point. However! Once you add more sources, you want to create one sub-pipeline for each source, and then run each of those pipelines from this pipeline. (We're thinking ahead! 😊)

### 10_Bronze_InsideAirbnb

This is the Pipeline where we ingest the files from InsideAirbnb:

![Pipelines](/Images/10_Bronze_01.png)

Wire up the Copy Activities:

![Pipelines](/Images/10_Bronze_02.png)

![Pipelines](/Images/10_Bronze_03.png)

Remember to set the compression on the Listings file:

![Pipelines](/Images/10_Bronze_04.png)

![Pipelines](/Images/10_Bronze_05.png)

▶️ Save all the Bronze pipelines and run the **10_Bronze** pipeline!

✅ Validate that you have the files in Bronze_Airbnb lakehouse.

🖱️ Load the files to tables. (⚠️ Remember to name the table **listings_details** for the notebooks to run without you having to make changes!):

![Pipelines](/Images/10_Bronze_06.png)

## 20_Silver

This Pipeline runs the Notebooks that loads the data from Bronze to Silver:

![Pipelines](/Images/20_Silver.png)

## 30_Gold

This Pipeline runs the Notebooks that loads the data from Silver to Gold:

![Pipelines](/Images/30_Gold.png)

## 00_Orchestration

This Pipeline runs the pipelines for each of our layers:

![Pipelines](/Images/00_Orchestration.png)

We have also added an Outlook task that will run if any of the pipelines fail.

## Questions?

If you have any questions, ping [Cathrine](https://www.linkedin.com/in/cathrinewilhelmsen/)! She'll be happy to help during or after SQLBits 🧡