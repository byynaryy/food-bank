# Food Bank Management System — Requirements Specification

**Version:** 0.1 (first draft) · **Status:** Draft, pending stakeholder validation

---

## Table of contents

1. [Project overview](#1-project-overview)
2. [Stakeholders and needs](#2-stakeholders-and-needs)
3. [Scope statement](#3-scope-statement)
4. [Conflicts, assumptions and open questions](#4-conflicts-assumptions-and-open-questions)
5. [System requirements (functional)](#5-system-requirements-functional)
6. [Non-functional requirements](#6-non-functional-requirements)
7. [Proposed user roles and access permissions](#7-proposed-user-roles-and-access-permissions)
8. [Key business rules](#8-key-business-rules)
9. [Key operational workflows](#9-key-operational-workflows)
10. [Initial acceptance criteria](#10-initial-acceptance-criteria)
11. [Recommended implementation priorities](#11-recommended-implementation-priorities)
12. [Items requiring stakeholder approval](#12-items-requiring-stakeholder-approval)
13. [Overall project success criteria](#13-overall-project-success-criteria)

---

## 1. Project overview

### 1.1 Background

The food bank is a volunteer-run organisation that distributes groceries to approximately **100 families** on a typical Saturday, with distribution taking place **twice a week**.

Its operations currently rely on several disconnected methods of communication and record-keeping:

- Paper sign-in sheets for family registration and attendance.
- A shared spreadsheet for inventory and volunteer information.
- A group chat for communicating stock movements, volunteer availability and operational updates.
- Léa's personal notebook for family information and dietary requirements.
- A whiteboard and printed documents for standard food packages and recipes.
- Verbal communication between volunteers during receiving, preparation and distribution.

These disconnected systems create problems with **information accuracy, communication, accountability and continuity**.

> **Example — inventory discrepancy:** The food bank believed it had approximately 40 kg of rice available on Thursday, but discovered on Saturday that only around 6 kg remained.

The discrepancy was caused by several unrecorded activities:

- Donations arriving without being properly sorted or recorded.
- Food being removed during Friday preparation.
- Large sacks being split into smaller portions without recording the conversion.
- Stock updates being delayed until Nadia had time to update the spreadsheet.

The organisation also relies heavily on individual volunteers' knowledge. Important operational information is often stored in people's memories, personal notebooks or informal conversations.

### 1.2 Project objectives

The proposed system aims to:

1. Provide one central place to access reliable operational information.
2. Improve inventory accuracy by recording important stock movements.
3. Make donation collection and receiving more organised.
4. Simplify food preparation and package tracking.
5. Improve family registration and attendance management.
6. Protect sensitive family and dietary information.
7. Improve volunteer coordination and role coverage.
8. Reduce Nadia's administrative workload.
9. Make operational procedures accessible when experienced volunteers are absent.
10. Provide reliable donation and waste-avoidance reporting.

---

## 2. Stakeholders and needs

The following sections identify the main stakeholders, their responsibilities, needs and expectations.

### 2.1 Internal stakeholders

| Stakeholder          | Role                                      | Main needs                                                                                                                                     |
| -------------------- | ----------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nadia**            | Coordinator and overall manager           | Central dashboard, reliable stock figures, oversight of operations, approval of exceptional decisions, reduced administration.                 |
| **Tom**              | Shift lead                                | Volunteer assignments, package preparation, recipe management, substitution records, distribution oversight and closing reconciliation.        |
| **Léa**              | Registration desk volunteer               | Fast family search, attendance tracking, household information, dietary restrictions, package allocation and backup registration support.      |
| **Samir**            | Donation collection driver                | Collection schedules, advance donation notifications, simple recording, transport preparation, clear acceptance rules and backup arrangements. |
| **Marguerite**       | Experienced receiving and stock volunteer | Simple receiving procedure, donation verification, stock checking, clear responsibilities and accessible records.                              |
| **Other volunteers** | Receiving, packing and distribution       | Simple instructions, minimal data entry, clear assignments and access to relevant operational information.                                     |

### 2.2 External stakeholders

| Stakeholder                        | Role                          | Main needs                                                                                                                                      |
| ---------------------------------- | ----------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| **Mr. Berger**                     | Partner grocery store manager | Reliable collection arrangements, one main contact, clear collection windows, minimal work for store staff and monthly donation weight reports. |
| **Grocery store department heads** | Identify surplus food         | Simple communication of available surplus without learning a new application.                                                                   |
| **Families receiving groceries**   | Beneficiaries                 | Correct package allocation, respect for dietary requirements, privacy and reliable distribution.                                                |

### 2.3 Stakeholder priorities

Not all stakeholders need access to the same information. The system should provide **role-appropriate access**. For example:

- **Nadia** needs an overall view of operations.
- **Tom** needs preparation and distribution information.
- **Léa** needs family information relevant to registration and package allocation.
- **Samir** needs collection and donation information.
- **Receiving volunteers** need donation verification and stock-entry functions.
- **Packing volunteers** need package contents and relevant dietary safeguards.
- **Mr. Berger** needs donation collection confirmation and reporting — not access to internal family or inventory records.

---

## 3. Scope statement

### 3.1 In scope

The first version of the system should focus on the following areas.

| Area                 | Included functionality                                                                            |
| -------------------- | ------------------------------------------------------------------------------------------------- |
| Dashboard            | Overview of stock, donations, upcoming collections, volunteer coverage and distribution activity. |
| Inventory management | Product records, quantities, units, stock movements and stock history.                            |
| Donation management  | Expected donations, collection records, receiving checks, accepted and rejected donations.        |
| Stock adjustments    | Record incoming stock, outgoing stock, repackaging, waste and corrections.                        |
| Food preparation     | Standard package recipes, package types and substitutions.                                        |
| Distribution         | Record packages prepared, distributed, uncollected and returned to stock.                         |
| Family management    | Family registration, unique identification, household size and package eligibility.               |
| Attendance           | Record family visits and grocery collection.                                                      |
| Dietary requirements | Secure recording and communication of allergies, religious restrictions and preferences.          |
| Volunteer management | Volunteer roles, availability, assignments and backup arrangements.                               |
| Reporting            | Donation weights, inventory summaries, distribution figures and discarded food.                   |
| User access          | Different access permissions based on volunteer responsibilities.                                 |
| Offline support      | Practical recording methods for areas with poor connectivity.                                     |
| Documentation        | Simple procedures and instructions for volunteers.                                                |

### 3.2 Out of scope

The following should **not** be included in the initial version unless stakeholders later approve an expansion.

| Area                                | Reason for exclusion                                                                |
| ----------------------------------- | ----------------------------------------------------------------------------------- |
| Financial accounting                | No identified requirement for managing budgets, expenses or financial transactions. |
| Online donations                    | The current project concerns physical food donations.                               |
| Grocery store inventory integration | Mr. Berger does not want store employees learning a new application.                |
| Automated food ordering             | The food bank primarily depends on surplus donations rather than purchasing stock.  |
| Family appointment booking          | Distribution currently operates without appointments.                               |
| Automated eligibility verification  | Families are not required to provide proof, and volunteers use discretion.          |
| Delivery services to families       | No existing home-delivery process was identified.                                   |
| Full volunteer recruitment platform | The immediate need is scheduling and operational coordination, not recruitment.     |
| Automated food safety decisions     | Acceptance and disposal decisions must follow approved human procedures.            |
| Replacement of all paper processes  | Some paper backups may remain necessary for accessibility and continuity.           |

### 3.3 Scope boundaries and assumptions

The proposed system will support the food bank's operations, but it will not automatically solve every operational problem.

> ⚠️ **Assumptions requiring validation:**
>
> - The food bank will continue to use volunteers with varying levels of technical ability.
> - Some activities will still need to be recorded on paper.
> - The back room may not have reliable internet access.
> - Nadia will remain responsible for approving important operational rules.
> - Some volunteers will need access to only a small part of the system.
> - The grocery store will continue communicating through existing channels such as phone calls and text messages.

---

## 4. Conflicts, assumptions and open questions

The stakeholder interviews identified several areas where people have different expectations, responsibilities are unclear, or important decisions have not yet been made. **These issues must be resolved before the system's final requirements and workflows are approved.**

### 4.1 Insurance and backup drivers

**Issue:** Samir is currently the only volunteer believed to be insured to drive the van.

- Nadia would like alternative drivers to cover collections.
- Samir is willing to have someone accompany him, particularly for lifting.
- It is unclear whether another volunteer can legally and safely drive the van under the existing insurance policy.

**Open questions:**

1. Does the current insurance policy permit other volunteers to drive?
2. Can additional drivers be added?
3. Who will cover collections when Samir is unavailable?
4. Who is responsible for confirming driver availability?

> 🔶 **Decision required:** Nadia must verify the insurance arrangements before alternative drivers are assigned.

### 4.2 Food safety and perishable donations

**Issue:** Samir currently transports chilled products without refrigerated equipment. The food bank also has limited cold-storage capacity.

- Nadia is willing to fund insulated boxes, ice packs and a fridge thermometer.
- Samir will use this equipment if it is prepared in advance.
- Mr. Berger expects chilled donations to be collected on the same day.
- Nadia does not want the food bank accepting more chilled food than it can safely accommodate.

**Open questions:**

1. What temperature limits and transport procedures apply to chilled and frozen donations?
2. How long can products safely remain in transport?
3. Who checks and records fridge and freezer temperatures?
4. What happens when a temperature is outside the approved range?
5. What are the rules for accepting products with damaged packaging or unclear labels?
6. Who has authority to reject or dispose of food?

> 🔶 **Decision required:** Nadia must obtain appropriate food safety guidance and establish documented procedures before the system implements acceptance rules.

### 4.3 Tuesday collection coverage

**Issue:** Mr. Berger proposed Tuesday and Friday collections, but Samir is generally unavailable on Tuesday mornings.

- Friday late morning is usually suitable for Samir.
- Nadia can occasionally cover Tuesday but cannot commit every week.
- No alternative driver has been confirmed.

**Open questions:**

1. Can another insured volunteer drive on Tuesdays?
2. Is there a reliable backup driver?
3. Could the store accommodate a different collection time?
4. Who will receive donations on Tuesdays?

> ✅ **Current decision:** Begin with **Friday collections only**. Tuesday collections remain a future possibility once reliable coverage is confirmed.

### 4.4 Ownership of recipes and package decisions

**Issue:** Nadia believes she owns the standard package recipes, but Tom makes practical adjustments during Friday preparation.

- Nadia established the original standard bag.
- Tom decides which substitutions are made according to available stock.
- The whiteboard and printed binder contain inconsistent versions.
- Some substitutions are based on Tom's judgement rather than documented rules.
- Baby formula cannot be substituted without approval.

**Open questions:**

1. Who has final authority over standard package recipes?
2. Can Tom approve routine substitutions independently?
3. Which substitutions are acceptable?
4. Which substitutions require Nadia's approval?
5. How should recipe changes be communicated to volunteers?
6. Should historical recipe versions be retained?

> 🔶 **Decision required:** Nadia and Tom must agree on recipe ownership, approval responsibilities and substitution rules.
>
> The system should distinguish between an **approved standard recipe** and the **actual contents of each package prepared**.

### 4.5 Léa's notebook and family data

**Issue:** Léa's notebook contains sensitive family information, including household details and dietary restrictions.

- Léa keeps the notebook at home because she fears losing it.
- Other volunteers cannot reliably access the information when she is absent.
- Some information is stored in the shared spreadsheet, but its accuracy is unclear.
- Allergies, religious restrictions and personal preferences are not always distinguished.
- Léa does not want sensitive information visible at the registration desk.

**Open questions:**

1. Who owns and controls family records?
2. Who is authorised to access dietary and allergy information?
3. Can packing volunteers see relevant restrictions without seeing other private family details?
4. How will family information be protected?
5. How will information be corrected or deleted?
6. How long should records be retained?
7. What is the procedure for handling a family member's request to update or remove information?
8. How will existing notebook information be transferred and checked?

> 🔶 **Decision required:** Nadia must approve a data-handling policy, including access permissions, retention, security and the treatment of sensitive information.

### 4.6 Additional unresolved issues

| Issue                        | Question requiring resolution                                                                                  |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------- |
| Receiving volunteers         | Who are the two or three authorised receiving volunteers?                                                      |
| Tuesday receiving            | Who receives donations if Tuesday collections resume?                                                          |
| Donation capacity            | How will acceptable storage limits be established?                                                             |
| Donation alternatives        | Can surplus food be redirected to another charity or organisation?                                             |
| Stock corrections            | Who can approve significant inventory corrections?                                                             |
| Free table                   | Who records food brought out from storage?                                                                     |
| Closing checks               | Who enters Saturday's closing figures into the system?                                                         |
| Family allocation            | Will Nadia formally approve Léa's flexible bag-allocation decisions?                                           |
| Monthly reporting            | Does the grocery store require a signed donation receipt or a particular reporting format?                     |
| Offline operation            | Should the system support offline digital recording, paper backups, or both?                                   |
| package for large households | Which package does a household of 6 or more receive, and how does BR-003 (babies) combine with household size? |

### 4.7 Decision log

The following decisions have already emerged from the interviews.

| Decision                    | Current position                                         |
| --------------------------- | -------------------------------------------------------- |
| Initial collection schedule | **Friday only**                                          |
| Tuesday collections         | **Postponed**                                            |
| Receiving responsibility    | Shared between two or three trained volunteers           |
| Receiving documentation     | One-page procedure                                       |
| Transport equipment         | Insulated boxes, ice packs and thermometer               |
| Additional fridge           | **Not affordable this year**                             |
| Oversized donations         | Prefer partial acceptance or refusal over unsafe storage |
| Donation recording          | Quick, simple process                                    |
| Family registration         | Printed backup required                                  |
| Family information          | Must have restricted access                              |
| Standard package recipes    | **Ownership still to be agreed**                         |

---

## 5. System requirements (functional)

The following requirements describe what the proposed system should do. Each requirement has a unique identifier and priority.

**Priority definitions:**

- **Must have** — Essential for the initial system to operate successfully.
- **Should have** — Important, but could be implemented after the core functionality.
- **Could have** — Useful improvement that is not essential initially.

### 5.1 Dashboard and overview

The dashboard should give Nadia a central overview of the food bank's operations.

| ID     | Requirement                                                                                | Priority    |
| ------ | ------------------------------------------------------------------------------------------ | ----------- |
| FR-001 | The system shall provide a central dashboard displaying important operational information. | Must have   |
| FR-002 | The dashboard shall display current inventory quantities.                                  | Must have   |
| FR-003 | The dashboard shall display upcoming and outstanding donations.                            | Should have |
| FR-004 | The dashboard shall display volunteer availability and assigned roles.                     | Should have |
| FR-005 | The dashboard shall display the number of packages prepared and distributed.               | Must have   |
| FR-006 | The dashboard shall highlight low-stock items and items requiring attention.               | Must have   |
| FR-007 | The dashboard shall display unresolved operational issues, such as unverified donations.   | Should have |
| FR-008 | The system shall provide different dashboard views depending on the user's role.           | Should have |

### 5.2 Inventory management

Inventory accuracy is one of the project's primary objectives.

| ID     | Requirement                                                                                                                   | Priority    |
| ------ | ----------------------------------------------------------------------------------------------------------------------------- | ----------- |
| FR-107 | The system shall track stock in lots. Each lot has a quantity, a unit, a received date and, where applicable, an expiry date. | Must have   |
| FR-009 | The system shall maintain a central inventory of food products.                                                               | Must have   |
| FR-010 | Each product shall have a name, category, quantity and unit of measurement.                                                   | Must have   |
| FR-011 | The system shall support different units, including kilograms, grams, individual items, boxes, crates and bags.               | Must have   |
| FR-012 | The system shall record stock received from donations.                                                                        | Must have   |
| FR-013 | The system shall record stock removed for package preparation.                                                                | Must have   |
| FR-014 | The system shall record stock returned after distribution.                                                                    | Must have   |
| FR-015 | The system shall record stock discarded, expired or damaged.                                                                  | Must have   |
| FR-016 | The system shall record repackaging and conversions between units.                                                            | Must have   |
| FR-017 | The system shall maintain a history of stock movements.                                                                       | Must have   |
| FR-018 | The system shall record the date and responsible user for each stock movement.                                                | Must have   |
| FR-019 | The system shall allow authorised users to correct inventory discrepancies.                                                   | Must have   |
| FR-020 | Significant stock corrections shall require an explanation.                                                                   | Should have |
| FR-021 | The system shall allow users to identify lots approaching their expiry dates.                                                 | Must have   |
| FR-022 | The system shall support stock checks and inventory reconciliation.                                                           | Must have   |
| FR-023 | The system shall allow low-stock thresholds to be configured for important products.                                          | Should have |

> **Specific rice-related requirement:** The system must support converting one 10 kg sack of rice into ten 1 kg portions, recording the reduction in bulk stock and the creation of smaller portions. This must **not** result in the rice being counted twice or disappearing from the inventory.

### 5.3 Donation management

| ID     | Requirement                                                                                                                 | Priority    |
| ------ | --------------------------------------------------------------------------------------------------------------------------- | ----------- |
| FR-024 | The system shall allow expected donations to be recorded.                                                                   | Must have   |
| FR-025 | Expected donations shall include the donor, estimated food categories, approximate quantities and expected collection date. | Must have   |
| FR-026 | The system shall distinguish between expected, collected, received and rejected donations.                                  | Must have   |
| FR-027 | The system shall record the volunteer responsible for collecting a donation.                                                | Must have   |
| FR-028 | The system shall record the number of crates or boxes collected.                                                            | Must have   |
| FR-029 | The system shall allow actual quantities to be verified when donations arrive.                                              | Must have   |
| FR-030 | The system shall record measured donation weights where applicable.                                                         | Must have   |
| FR-031 | The system shall distinguish measured weights from estimated weights.                                                       | Must have   |
| FR-032 | The system shall record partially accepted and rejected donations.                                                          | Must have   |
| FR-033 | The system shall record reasons for refusing or discarding donations.                                                       | Must have   |
| FR-034 | The system shall provide a donation history for each partner organisation.                                                  | Should have |
| FR-035 | The system shall generate monthly donation weight reports.                                                                  | Must have   |
| FR-036 | The system shall support recording donation receipt information, including date and weight.                                 | Should have |

### 5.4 Receiving and storage management

| ID     | Requirement                                                                                          | Priority    |
| ------ | ---------------------------------------------------------------------------------------------------- | ----------- |
| FR-037 | The system shall identify authorised receiving volunteers.                                           | Must have   |
| FR-038 | The system shall provide a standard donation-receiving checklist.                                    | Must have   |
| FR-039 | The receiving process shall allow volunteers to record donations using a short, simple workflow.     | Must have   |
| FR-040 | The system shall distinguish between collected goods and goods verified and accepted into inventory. | Must have   |
| FR-041 | The system shall record the condition and relevant expiry information of received products.          | Must have   |
| FR-042 | The system shall record the storage location of products where practical.                            | Should have |
| FR-043 | The system shall support monitoring of fridge and freezer temperatures.                              | Should have |
| FR-044 | The system shall identify donations requiring special handling or storage.                           | Must have   |
| FR-045 | The system shall provide a way to record storage-related rejection decisions.                        | Must have   |
| FR-046 | The system shall support recording who verified and accepted a donation.                             | Must have   |

> **Important:** The system must **not** automatically declare food safe based solely on a recorded temperature or expiry date. Approved food safety procedures must determine acceptance and handling.

### 5.5 Food preparation and recipes

| ID     | Requirement                                                                   | Priority    |
| ------ | ----------------------------------------------------------------------------- | ----------- |
| FR-047 | The system shall maintain standard recipes for each package type.             | Must have   |
| FR-048 | The system shall support small, large and baby packages.                      | Must have   |
| FR-049 | Each recipe shall specify the expected products and quantities.               | Must have   |
| FR-050 | The system shall identify approved substitutions.                             | Must have   |
| FR-051 | The system shall record actual substitutions made during preparation.         | Must have   |
| FR-052 | The system shall record the actual contents of packages prepared.             | Must have   |
| FR-053 | The system shall allow authorised users to update recipes.                    | Must have   |
| FR-054 | The system shall retain previous recipe versions.                             | Should have |
| FR-055 | The system shall distinguish substitutions requiring special approval.        | Must have   |
| FR-056 | The system shall prevent unapproved formula substitutions.                    | Must have   |
| FR-057 | The system shall generate a simple package contents checklist for volunteers. | Must have   |
| FR-058 | The system shall record the number of packages prepared by package type.      | Must have   |

> **Important distinction:** The **standard recipe** describes what _should_ be packed. The **preparation record** describes what was _actually_ packed. Both are needed to maintain accurate stock figures.

### 5.6 Family registration and management

| ID     | Requirement                                                                             | Priority    |
| ------ | --------------------------------------------------------------------------------------- | ----------- |
| FR-059 | The system shall allow authorised volunteers to register new families.                  | Must have   |
| FR-060 | The system shall assign each family a unique reference number.                          | Must have   |
| FR-061 | The system shall allow family records to be searched by name or reference number.       | Must have   |
| FR-062 | The search function shall accommodate minor spelling differences.                       | Should have |
| FR-063 | The system shall record household size.                                                 | Must have   |
| FR-064 | The system shall record relevant household information needed for package allocation.   | Must have   |
| FR-065 | The system shall allow authorised volunteers to update family information.              | Must have   |
| FR-066 | The system shall maintain a history of important changes to family records.             | Should have |
| FR-067 | The system shall support family records being accessed by authorised backup volunteers. | Must have   |
| FR-068 | The system shall avoid unnecessary collection of personal information.                  | Must have   |

### 5.7 Dietary requirements and family safety

| ID     | Requirement                                                                                                      | Priority    |
| ------ | ---------------------------------------------------------------------------------------------------------------- | ----------- |
| FR-069 | The system shall allow dietary restrictions to be recorded for each family.                                      | Must have   |
| FR-070 | The system shall distinguish allergies from religious restrictions and personal preferences.                     | Must have   |
| FR-071 | The system shall allow authorised users to update dietary information.                                           | Must have   |
| FR-072 | The system shall flag relevant dietary requirements during package preparation.                                  | Must have   |
| FR-073 | The system shall allow packing volunteers to view only the information necessary to prepare the correct package. | Must have   |
| FR-074 | The system shall record when a dietary restriction is updated.                                                   | Should have |
| FR-075 | The system shall support special package identification without exposing unnecessary personal details.           | Must have   |
| FR-076 | The system shall allow a package to be checked again when a new allergy is reported after preparation.           | Must have   |

### 5.8 Attendance and distribution

| ID     | Requirement                                                                                            | Priority    |
| ------ | ------------------------------------------------------------------------------------------------------ | ----------- |
| FR-077 | The system shall record family attendance at each distribution session.                                | Must have   |
| FR-078 | The system shall indicate whether a family has already collected groceries during the current session. | Must have   |
| FR-079 | The system shall record the package type allocated to each family.                                     | Must have   |
| FR-080 | The system shall record whether the package was actually collected.                                    | Must have   |
| FR-081 | The system shall allow authorised volunteers to record exceptional package allocations.                | Must have   |
| FR-082 | The system shall record packages prepared but not collected.                                           | Must have   |
| FR-083 | The system shall record packages returned to stock or dismantled.                                      | Must have   |
| FR-084 | The system shall support recording food removed from the free table's storage.                         | Should have |
| FR-085 | The system shall support a simple closing reconciliation.                                              | Must have   |

### 5.9 Volunteer management

| ID     | Requirement                                                                        | Priority    |
| ------ | ---------------------------------------------------------------------------------- | ----------- |
| FR-086 | The system shall maintain a list of volunteers and their contact details.          | Should have |
| FR-087 | The system shall record volunteer roles and relevant skills.                       | Should have |
| FR-088 | The system shall allow volunteers to record availability.                          | Should have |
| FR-089 | The system shall allow authorised users to assign volunteers to operational roles. | Should have |
| FR-090 | The system shall identify roles without sufficient volunteer coverage.             | Should have |
| FR-091 | The system shall support backup volunteer assignments.                             | Should have |
| FR-092 | The system shall allow volunteer assignments to be printed.                        | Should have |
| FR-093 | The system shall support volunteers who cannot or do not want to use a smartphone. | Must have   |

### 5.10 Reporting

| ID     | Requirement                                                                   | Priority    |
| ------ | ----------------------------------------------------------------------------- | ----------- |
| FR-094 | The system shall generate inventory reports.                                  | Must have   |
| FR-095 |                                                                               | Must have   |
| FR-096 | The system shall report the number of families served.                        | Must have   |
| FR-097 | The system shall report packages prepared, distributed and uncollected.       | Must have   |
| FR-098 | The system shall report discarded and expired food.                           | Must have   |
| FR-099 | The system shall allow authorised users to review historical stock movements. | Must have   |
| FR-100 | The system shall allow reports to be exported or printed.                     | Should have |

### 5.11 User roles and permissions

| ID     | Requirement                                                                                 | Priority  |
| ------ | ------------------------------------------------------------------------------------------- | --------- |
| FR-101 | The system shall support different user roles.                                              | Must have |
| FR-102 | The system shall restrict access according to assigned permissions.                         | Must have |
| FR-103 | The system shall allow Nadia to manage user permissions.                                    | Must have |
| FR-104 | The system shall restrict access to sensitive family information.                           | Must have |
| FR-105 | The system shall record important changes made by users.                                    | Must have |
| FR-106 | The system shall allow authorised backup volunteers to perform designated responsibilities. | Must have |

---

## 6. Non-functional requirements

These requirements describe how the system should operate, rather than the specific functions it performs. Given the volunteers' different levels of technical ability and the food bank's working conditions, these are particularly important.

| ID      | Requirement                                                                                                                              | Priority    |
| ------- | ---------------------------------------------------------------------------------------------------------------------------------------- | ----------- |
| NFR-001 | The system shall have a simple and intuitive interface suitable for volunteers with limited technical experience.                        | Must have   |
| NFR-002 | Common actions shall require minimal steps and avoid lengthy forms.                                                                      | Must have   |
| NFR-003 | Text, buttons and controls shall be sufficiently large and readable for older users.                                                     | Must have   |
| NFR-004 | The system shall support operation in areas with unreliable internet connectivity.                                                       | Must have   |
| NFR-005 | Information entered offline shall be synchronised when connectivity becomes available, without silently overwriting conflicting changes. | Must have   |
| NFR-006 | The system shall provide a practical paper-based backup procedure.                                                                       | Must have   |
| NFR-007 | The system shall protect sensitive information against unauthorised access.                                                              | Must have   |
| NFR-008 | The system shall maintain reliable and accurate inventory records.                                                                       | Must have   |
| NFR-009 | The system shall provide clear confirmation when important information has been saved.                                                   | Must have   |
| NFR-010 | Family search results shall appear quickly enough to support busy registration periods.                                                  | Must have   |
| NFR-011 | The system shall be accessible from appropriate devices available to the organisation.                                                   | Should have |
| NFR-012 | The system shall provide a record of significant data changes.                                                                           | Must have   |
| NFR-013 | The system shall support regular data backups and recovery.                                                                              | Must have   |
| NFR-014 | The system shall be maintainable without requiring specialist technical knowledge for routine administration.                            | Should have |
| NFR-015 | The system shall avoid requiring volunteers to enter the same information into multiple places.                                          | Must have   |

### 6.1 Usability expectations

The following practical expectations should guide interface design:

- A volunteer should be able to record a straightforward donation in approximately one minute.
- A volunteer should be able to record a package-preparation batch without entering every individual product manually.
- Léa should be able to locate a returning family quickly.
- A volunteer should be able to complete a closing checklist in approximately five minutes.
- The system should use straightforward language rather than technical terminology.
- Important actions should have clear labels rather than relying exclusively on icons.
- Volunteers should have access to simple printed instructions.

> 💡 These are **proposed usability targets** and should be tested with actual volunteers.

---

## 7. Proposed user roles and access permissions

The following is an **initial permissions model**. It needs approval from Nadia.

| Role                                            | Suggested access                                                                                |
| ----------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| **Coordinator (Nadia)**                         | Full operational access, approvals, reports and user management.                                |
| **Shift lead (Tom)**                            | Package preparation, recipes, substitutions, volunteer assignments and distribution.            |
| **Registration volunteer (Léa)**                | Family registration, attendance, household information and relevant dietary restrictions.       |
| **Collection volunteer (Samir)**                | Collection schedules, donation notifications and collection records.                            |
| **Receiving volunteer (Marguerite and others)** | Donation verification, stock entry, expiry checks and receiving records.                        |
| **Packing volunteer**                           | Package recipes, actual contents and necessary dietary safeguards.                              |
| **General volunteer**                           | Only the operational information required for their assigned duties.                            |
| **External partner (Mr. Berger)**               | No direct system access in the initial version; existing communication methods remain in place. |

> 🔒 **Important:** Access to sensitive family information should be restricted **independently of general volunteer permissions**. For example, a packing volunteer might need to know that a particular package must not contain peanuts, without needing to see the family's name, address or personal circumstances.

---

## 8. Key business rules

These rules describe how the food bank currently operates or how it intends to operate. **Some are provisional and require confirmation.**

| ID     | Business rule                                                                                                          |
| ------ | ---------------------------------------------------------------------------------------------------------------------- |
| BR-001 | Families with one or two household members generally receive small packages. **Note:** Incomplete: see section 4.6.    |
| BR-002 | Families with three to five household members generally receive large packages. **Note:** Incomplete: see section 4.6. |
| BR-003 | Families with babies may receive baby packages.                                                                        |
| BR-004 | Baby formula must not be substituted with a different type without an approved procedure.                              |
| BR-005 | Package substitutions must be recorded using the actual replacement product.                                           |
| BR-006 | Food must not be accepted if it cannot be transported or stored safely.                                                |
| BR-007 | Donation rejection decisions must follow rules approved by Nadia.                                                      |
| BR-008 | Significant stock corrections must include an explanation.                                                             |
| BR-009 | Food disposal requires Nadia's approval or an agreed delegated procedure.                                              |
| BR-010 | Family attendance must be recorded when groceries are collected.                                                       |
| BR-011 | A family should not accidentally receive duplicate packages during the same distribution session.                      |
| BR-012 | Uncollected packages must be checked before their contents are returned to stock.                                      |
| BR-013 | Allergies must be distinguished from religious restrictions and personal preferences.                                  |
| BR-014 | Family information must only be accessible to authorised volunteers.                                                   |
| BR-015 | Actual package contents must be recorded when substitutions occur.                                                     |

---

## 9. Key operational workflows

These workflows provide an initial picture of how the proposed system should support the food bank.

### 9.1 Donation workflow

1. Grocery store notifies the food bank about expected surplus.
2. Food bank confirms whether collection can be arranged.
3. An authorised volunteer is assigned.
4. Transport equipment is prepared.
5. Volunteer collects the donation.
6. Donation is delivered to the food bank.
7. A receiving volunteer verifies the contents.
8. Accepted quantities are weighed or counted as appropriate.
9. Stock records are updated.
10. Rejected or discarded products are recorded.

### 9.2 Package preparation workflow

1. Tom selects the package type being prepared.
2. System displays the approved recipe.
3. Volunteers prepare the required number of packages.
4. Any substitutions are selected and recorded.
5. Actual package contents are confirmed.
6. Stock quantities are reduced according to actual usage.
7. Prepared package quantities are recorded.

### 9.3 Family distribution workflow

1. Family arrives at the registration desk.
2. Léa searches for the family using its name or reference number.
3. System displays relevant household information.
4. Léa confirms the package type.
5. Dietary requirements are communicated securely to the packing team.
6. Family receives the appropriate package.
7. Attendance and collection are recorded.
8. Uncollected packages are reconciled after distribution.

### 9.4 Closing reconciliation workflow

1. Remaining packages are counted.
2. Fresh and refrigerated products are separated for appropriate checks.
3. Reusable packages are identified.
4. Reusable food is returned to stock.
5. Non-reusable food is recorded for appropriate disposal.
6. Free-table stock brought out from storage is accounted for where practical.
7. Closing figures are recorded and made available to Nadia.

---

## 10. Initial acceptance criteria

These criteria will help determine whether the first version of the system actually solves the problems identified during interviews.

| Area                 | Proposed acceptance criterion                                                                                             |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| Inventory            | A stock movement can be recorded and reflected in the current stock balance.                                              |
| Repackaging          | Splitting a 10 kg rice sack into 1 kg portions correctly updates both quantities.                                         |
| Donations            | A donation can be recorded as expected, collected, verified and accepted.                                                 |
| Receiving            | A receiving volunteer can complete the basic checklist in approximately one minute.                                       |
| Stock accuracy       | Unrecorded or unverified stock movements can be identified through reconciliation.                                        |
| Recipes              | Volunteers can see the approved package recipe and record substitutions.                                                  |
| Family search        | Léa can find an existing family using a name or reference number.                                                         |
| Attendance           | The system identifies families who have already collected groceries that session.                                         |
| Dietary requirements | Relevant restrictions are available to authorised packing volunteers without exposing unnecessary personal information.   |
| Leftovers            | Prepared, distributed, uncollected and returned packages can be distinguished.                                            |
| Reporting            | Nadia can generate a monthly donation weight report.                                                                      |
| Offline operation    | Essential receiving information can be captured without an internet connection and reconciled later.                      |
| Usability            | Volunteers with different levels of technical experience can complete their assigned tasks following simple instructions. |

---

## 11. Recommended implementation priorities

The food bank has many operational problems, but the first release should concentrate on making its most important information reliable. Not everything should be built at once.

### Phase 1 · Essential — Reliable inventory and donation management

- Central product inventory.
- Donation recording and verification.
- Stock movement history.
- Repackaging and unit conversions.
- Basic package recipes and substitutions.
- Simple receiving checklist.

### Phase 2 · Distribution — Family and package management

- Family registration.
- Attendance tracking.
- Household information.
- Dietary requirements and access controls.
- Package contents and distribution records.
- Leftover reconciliation.

### Phase 3 · Coordination — Volunteer and operational management

- Volunteer availability.
- Shift assignments.
- Backup role coverage.
- Collection scheduling.
- Storage monitoring.
- Expanded reporting and dashboard.

> ⚠️ **Note:** The phases are provisional. In particular, **dietary safeguards and the security of family information should be designed from the beginning**, not postponed until Phase 2.

---

## 12. Items requiring stakeholder approval

Before this specification becomes final, a short validation meeting should be arranged with **Nadia and Tom**, followed by confirmation from **Léa and Samir** on their respective workflows.

The following decisions are particularly important:

| Decision                                       | Stakeholder responsible      | Status |
| ---------------------------------------------- | ---------------------------- | ------ |
| Confirm van insurance and alternative drivers  | Nadia                        | Open   |
| Approve food safety and temperature procedures | Nadia                        | Open   |
| Confirm Tuesday collection arrangements        | Nadia / Mr. Berger           | Open   |
| Agree on recipe ownership                      | Nadia / Tom                  | Open   |
| Approve substitution rules                     | Nadia / Tom                  | Open   |
| Approve family data access and retention rules | Nadia                        | Open   |
| Decide how Léa's notebook will be handled      | Nadia / Léa                  | Open   |
| Identify additional receiving volunteers       | Nadia                        | Open   |
| Establish storage capacity limits              | Nadia / receiving volunteers | Open   |
| Confirm donation reporting format              | Mr. Berger / Nadia           | Open   |
| Confirm package allocation rules               | Nadia / Léa                  | Open   |

---

## 13. Overall project success criteria

The project should be considered successful when:

1. Nadia can see reliable inventory information without manually combining several records.
2. Donations are recorded and verified before being treated as available stock.
3. Food movements during preparation are accounted for.
4. Volunteers can follow standard package recipes and record substitutions.
5. Léa can register families and record attendance without relying exclusively on her personal notebook.
6. Dietary restrictions are communicated accurately and privately.
7. Uncollected packages are reconciled with stock.
8. Donations are not accepted beyond the food bank's safe transport and storage capacity.
9. Volunteers can perform their responsibilities without needing Nadia to explain every procedure.
10. The system reduces administrative work rather than creating another layer of paperwork.

---

_End of first draft — Version 0.1_
