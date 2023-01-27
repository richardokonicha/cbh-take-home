# Ticket Breakdown
We are a staffing company whose primary purpose is to book Agents at Shifts posted by Facilities on our platform. We're working on a new feature which will generate reports for our client Facilities containing info on how many hours each Agent worked in a given quarter by summing up every Shift they worked. Currently, this is how the process works:

- Data is saved in the database in the Facilities, Agents, and Shifts tables
- A function `getShiftsByFacility` is called with the Facility's id, returning all Shifts worked that quarter, including some metadata about the Agent assigned to each
- A function `generateReport` is then called with the list of Shifts. It converts them into a PDF which can be submitted by the Facility for compliance.

## You've been asked to work on a ticket. It reads:

**Currently, the id of each Agent on the reports we generate is their internal database id. We'd like to add the ability for Facilities to save their own custom ids for each Agent they work with and use that id when generating reports for them.**


Based on the information given, break this ticket down into 2-5 individual tickets to perform. Provide as much detail for each ticket as you can, including acceptance criteria, time/effort estimates, and implementation details. Feel free to make informed guesses about any unknown details - you can't guess "wrong".


You will be graded on the level of detail in each ticket, the clarity of the execution plan within and between tickets, and the intelligibility of your language. You don't need to be a native English speaker, but please proof-read your work.

## Your Breakdown Here

###### Ticket 1: Add custom Agent id field to Facility table

###### Acceptance Criteria:
* A new field called "custom_agent_id" is added to the Facility table in the database
* The field is of type string and has a maximum length of 50 characters
* The field is nullable and is not required to have a value
###### Time/Effort Estimate: 2 hours
###### Implementation Details:
* Update the Facility table in the database by adding the custom_agent_id field
* Update any relevant database queries or models to account for the new field
* Update any relevant forms or views to allow Facilities to input their own custom ids for Agents

###### Ticket 2: Update generateReport function to use custom Agent id

###### Acceptance Criteria:
* The generateReport function is updated to use the custom_agent_id field from the Facility table instead of the internal database id for Agents when generating reports
* If the custom_agent_id field is null or empty, the internal database id should be used instead
###### Time/Effort Estimate: 4 hours
###### Implementation Details:
* Update the generateReport function to retrieve the custom_agent_id for each Agent from the Facility table
* Update the function to use the custom_agent_id when generating reports, and fall back to the internal database id if necessary
* Test the function to ensure that it correctly generates reports using the custom Agent id
###### Ticket 3: Update getShiftsByFacility function to include custom Agent id

###### Acceptance Criteria:
* The getShiftsByFacility function is updated to include the custom_agent_id field from the Facility table in the metadata it returns for each Agent
* If the custom_agent_id field is null or empty, the internal database id should be returned instead
###### Time/Effort Estimate: 2 hours
###### Implementation Details:
Update the getShiftsByFacility function to retrieve the custom_agent_id for each Agent from the Facility table
* Update the function to include the custom_agent_id in the metadata it returns for each Agent, and fall back to the internal database id if necessary
* Test the function to ensure that it correctly includes the custom Agent id in the metadata it returns
##### Ticket 4: Update Shift table to include custom Agent id

###### Acceptance Criteria:
* A new field called "custom_agent_id" is added to the Shift table in the database
* The field is of type string and has a maximum length of 50 characters
* The field is nullable and is not required to have a value
###### Time/Effort Estimate: 2 hours
###### Implementation Details:
* Update the Shift table in the database by adding the custom_agent_id field
* Update any relevant database queries or models to account for the new field
* Update any relevant forms or views to allow input of custom Agent ids for each Shift
###### Ticket 5: Update getShiftsByFacility function to use custom Agent id

###### Acceptance Criteria:
* The getShiftsByFacility function is updated to use the custom_agent_id field from the Shift table instead of the internal database id for Agents when generating reports
* If the custom_agent_id field is null or empty, the internal database id should be used instead
###### Time/Effort Estimate: 2 hours
###### Implementation Details:
* Update the getShiftsByFacility function to retrieve the custom_agent_

---