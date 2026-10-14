Splunk Threat Investigation: Multiple Failed Login Attempts

Project Overview

This project documents a threat investigation using Splunk Enterprise to examine multiple failed login attempts in the BetterBytes log dataset. The investigation focused on identifying repeated authentication failures, examining activity associated with a specific IP address, and organising the results for incident reporting.

Objective

To investigate failed login events in Splunk, identify suspicious authentication patterns, narrow the results to a specific source IP address, and export the findings for documentation.

Tools Used

* Splunk Enterprise
* BetterBytes log dataset
* Splunk Search & Reporting

Investigation Methodology

Step 1: Upload the Log Data

Navigated to Add Data in Splunk Enterprise and uploaded the BetterBytes log archive.

Step 2: Configure Input Settings

Reviewed the input settings before completing the upload. The source type was set to Automatic, and the host setting was configured to use a regular expression for the source path.

Step 3: Review and Complete the Upload

Reviewed the input configuration and submitted the data for ingestion into Splunk.

Step 4: Start Searching

Selected Start Searching to access the ingested log events in Splunk Search & Reporting.

Step 5: Filter Failed Login Events

Used the search query below to narrow the results to events containing the failure pattern:

source="BetterBytes Log Files.zip:"fail

The search returned 166,265 events in the displayed results.

Step 6: Set the Time Range

Selected the Last 30 days time range to narrow the investigation to the relevant period shown in the Splunk interface.

Step 7: Examine Authentication Failures

Reviewed the returned events and observed failed password attempts involving different usernames from the same source IP address. This pattern warranted further investigation.

Step 8: Investigate the Source IP Address

Refined the search by adding the IP address 64.66.0.20 to the failed-event search.

The refined search returned 655 events in the displayed results. The logs included failed password attempts for usernames such as inet and mailman.

Step 9: Create a Table View

Selected Create Table View to organise the search results into a tabular format for review and documentation.

Step 10: Save the Table View

Selected Save to save the table view.

Step 11: Review the Saved Results

Opened the saved table view and selected the relevant time range to review the investigation results.

Step 12: Export the Results

Exported the table results using the CSV format, which was selected by default in the export dialog.

Key Observations

* The initial search returned a large volume of events containing the failure pattern.
* Multiple failed password attempts were associated with the source IP address 64.66.0.20.
* The displayed events included attempts involving different usernames, including inet and mailman.
* The refined search returned 655 events in the displayed results.
* The results were organised into a table and exported in CSV format for documentation.

Conclusion

This project demonstrates a basic threat investigation workflow in Splunk Enterprise, including log ingestion, search filtering, time-range selection, source IP investigation, table creation, and CSV export.

The observed authentication failures and use of different usernames from the same IP address may indicate password-guessing or brute-force activity. However, the available evidence alone does not confirm a successful compromise or establish the attacker’s identity.

Evidence

Screenshots documenting the data upload, search filters, failed login events, table creation, and exported results are included in this repository.

Disclaimer

This project documents analysis of the supplied BetterBytes log dataset for learning and portfolio purposes. Findings are limited to the events and screenshots reviewed during the investigation.
