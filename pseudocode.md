# WaterWatch SL - Pseudocode

This file contains language-independent pseudocode for the PROG101 logical-design assignment. It is not executable source code.

```text
CONSTANT DUPLICATE_WINDOW_HOURS = 48
CONSTANT AFFECTED_USER_THRESHOLD = 100  // configurable pilot value

PROCEDURE SubmitWaterFaultReport()
    INPUT community, waterPointID, faultType, urgency
    INPUT facilityType, affectedUsers, reporterContact

    validReport = ValidateRequiredFields(community, waterPointID,
                                         faultType, urgency, affectedUsers)
    WHILE validReport = FALSE
        DISPLAY "Please complete or correct the required fields."
        INPUT community, waterPointID, faultType, urgency
        INPUT facilityType, affectedUsers, reporterContact
        validReport = ValidateRequiredFields(community, waterPointID,
                                             faultType, urgency, affectedUsers)
    END WHILE

    existingCaseID = FindMatchingOpenCase(waterPointID, faultType,
                                           DUPLICATE_WINDOW_HOURS)
    IF existingCaseID IS NOT EMPTY THEN
        AppendUpdate(existingCaseID, "Additional report received")
        caseID = existingCaseID
        priority = CalculatePriority(faultType, urgency, facilityType, affectedUsers)
        UpdatePriorityIfMoreUrgent(caseID, priority)
        IF priority = "HIGH" THEN NotifyResponsibleOfficer(caseID, priority) END IF
    ELSE
        caseID = GenerateUniqueCaseID()
        priority = CalculatePriority(faultType, urgency, facilityType, affectedUsers)
        SaveNewCase(caseID, community, waterPointID, faultType, urgency,
                     affectedUsers, priority, CURRENT_DATETIME)
        SetStatus(caseID, "NEW")
        NotifyResponsibleOfficer(caseID, priority)
    END IF

    DISPLAY "Case ID: ", caseID
END PROCEDURE

FUNCTION CalculatePriority(faultType, urgency, facilityType, affectedUsers)
    IF faultType = "SUSPECTED CONTAMINATION" OR urgency = "CRITICAL" THEN
        RETURN "HIGH"
    ELSE IF facilityType = "SCHOOL" OR facilityType = "HEALTH FACILITY"
         OR affectedUsers >= AFFECTED_USER_THRESHOLD THEN
        RETURN "MEDIUM"
    ELSE
        RETURN "LOW"
    END IF
END FUNCTION

PROCEDURE ReviewOpenCases()
    FOR EACH case IN OpenCaseQueue
        IF case.priority = "HIGH" AND case.status = "NEW" THEN
            FlagForPromptReview(case.caseID)
        END IF
        IF case.lastUpdated exceeds the local follow-up interval THEN
            AddToFollowUpList(case.caseID)
        END IF
    END FOR
END PROCEDURE
```

**Design note:** The value of 100 affected users and the 48-hour duplicate window are illustrative and configurable; the responsible local team should review both before a pilot. WaterWatch SL records and routes reports; it does not independently test water or declare water safe/unsafe.
