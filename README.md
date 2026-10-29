# PROG101_Assignment1_Peter-C-Wurie_905006243
[README.md](https://github.com/user-attachments/files/34119014/README.md)

# WaterWatch SL - PROG101 Assignment

**Project title:** WaterWatch SL: A Community Water Point Fault Reporting and Maintenance Tracking System  
**Course:** PROG101 - Principles of Programming Logic and Design  
**Student:** [Student Full Name]  
**Student ID:** [Student ID]  

## Problem addressed
WaterWatch SL proposes a standard way for residents and community focal persons to report faults at shared water points, receive a case reference, and track whether the report has been reviewed or resolved. The design prioritises validation, duplicate detection, transparent triage and status tracking. It does not test water quality or replace maintenance staff.

## Included files
- `Report/WaterWatch_SL_Assignment.docx` - editable report.
- `Report/WaterWatch_SL_Assignment.pdf` - printable report draft; regenerate it after replacing student details.
- `Flowcharts/flowchart.png` and `Flowcharts/flowchart.pdf` - main submission flowchart.
- `Pseudocode/pseudocode.md` - pseudocode for the logical design.

## Main logical flow
1. Capture the location and fault details.
2. Validate mandatory fields.
3. Search for a similar unresolved report within the configurable duplicate window.
4. Reuse the existing case ID or generate a new one.
5. Classify priority. Suspected contamination or critical urgency is HIGH; otherwise, school/health facility or a configurable affected-user threshold is MEDIUM; other cases are LOW.
6. Save and refer the report, display the case ID, and allow authorised status updates.

## Design assumptions
- Duplicate window: 48 hours for the initial design; configurable.
- Affected-user threshold: 100 for illustration only; it must be reviewed by local operators.
- Reporting may be assisted or entered from paper/phone reports where connectivity is limited. SMS/USSD support is a possible future enhancement, not a feature claimed to exist in this assignment.
- Reporter contact details are optional, subject to local procedures and privacy protections.

## SDG alignment
The primary alignment is SDG 6: Clean Water and Sanitation, especially target 6.1 (safe and affordable drinking water) and target 6.b (community participation in water and sanitation management). The system contributes indirectly by improving reporting and follow-up information.

## Open-source and Digital Public Goods approach
A future implementation could be published under a recognised open-source licence after ownership and licensing are confirmed. To progress toward Digital Public Goods recognition, it would need to satisfy the Digital Public Goods Standard, including open licensing, clear ownership, documentation, platform independence, data export, privacy and security requirements. It is not claimed to be certified or listed as a DPG.

## References
- Digital Public Goods Alliance. (n.d.). [Digital Public Goods Standard](https://www.digitalpublicgoods.net/standard).
- Ministry of Water Resources and Sanitation. (2026). *National Water Compact for Sierra Leone 2026-2030*. [PDF](https://www.worldbank.org/content/dam/theworldbankgroupasset/document/2026/water-forward-compacts/Water%20Compact%20Sierra%20Leone%202026.pdf).
- UNICEF Sierra Leone. (2026, February 5). [Access to clean water could improve children’s health and education](https://www.unicef.org/sierraleone/stories/access-clean-water-could-improve-childrens-health-and-education).
- United Nations, Department of Economic and Social Affairs. (n.d.). [Goal 6: Clean Water and Sanitation](https://sdgs.un.org/goals/goal6).

 
