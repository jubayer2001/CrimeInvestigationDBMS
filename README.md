# CrimeInvestigationDBMS
The crime Investigation Database is created using Microsoft SQL Server.


###  **Database Name: `crime_investigation`**

This database is designed to manage various aspects of police operations, case investigations, and legal proceedings. It tracks everything from police stations and officers to FIRs, GDs, suspects, victims, and court hearings.

---

###  **Entities and Their Purpose**

1. **`Police_Station`**

   * Stores details of police stations including name, address, and contact number.
   * Primary key: `station_id`

2. **`Police_Officer`**

   * Information about officers including rank, contact, and the station they belong to.
   * References `Police_Station` via `station_id`.

3. **`Station_vehicle`**

   * Tracks vehicles assigned to stations and officers.
   * Linked to both `Police_Station` and `Police_Officer`.

4. **`Complainant`**

   * Stores citizen data who report crimes or file GDs/FIRs.
   * Fields: name, contact, address, and email.

5. **`GD (General Diary)`**

   * Used for recording non-criminal matters (e.g., lost items).
   * References `Police_Officer`, `Police_Station`, and `Complainant`.

6. **`Victim`**

   * Details of individuals affected by crimes.
   * Contains contact info and a description field.

7. **`Criminal`**

   * Contains known criminals’ data like name, alias, and DOB.

8. **`Suspect`**

   * Stores details of individuals suspected in cases (not yet confirmed criminals).

9. **`Witness`**

   * Contains witnesses' personal info and their statements.
   * Meant to support investigation and court proceedings.

10. **`Evidence`**

    * Tracks evidence items collected in cases.
    * Each item references the officer who collected it.

11. **`Court`**

    * Basic court details including name and address.

12. **`Hearing`**

    * Stores information about court hearings including date, verdict, judge, and related suspect/criminal.
    * References `Court`, `Suspect`, and `Criminal`.

13. **`Case_status`**

    * Maintains the status and update date of a case (e.g., ongoing, closed).

14. **`FIR (First Information Report)`**

    * Used for officially starting a criminal investigation.
    * References complainant, officer, and station.

15. **`Case_`**

    * Central table combining information about an ongoing case.
    * References FIR, officer, witness, suspect, victim, evidence, hearing, and status.

16. **`Investigation_team`**

    * Represents groups of officers working on a case.
    * Each team has a leader, member, and associated case.

---



### 🧩 **Design Strengths**

* Well-normalized: avoids data duplication.
* Foreign keys enforce referential integrity.
* Covers a full investigation cycle: from report to trial.

