# COBOL-Banking-Tranzactions-Processing-Project--

This COBOL project is designed to process input records from an input file and generate output records based on specific business rules. The program reads data from INP-FILE and processes it, updating information from COM-FILE, and then writes the results to OUT-FILE and REP-FILE. Here's a detailed description of the project structure and logic:
Project Structure:
Identification Division:

    Program ID: COBFILE2

Environment Division:

    Configuration Section: Configures special names and file connections.
    Input-Output Section: Defines file structures and their statuses.

Data Division:

    File Section: Describes the input (INP-FILE), output (OUT-FILE, REP-FILE), and reject (REJ-FILE) file formats.
    Working-Storage Section: Contains working variables and flags for validation and processing.
    Copy Sections: Include copybooks (e.g., CPYCOM, CPYINP1, CPYOUT1, CPYREJ1) containing schema definitions and other data structures.

Procedure Division:

    Open Files: Opens input, output, and commission files.
    Write Headers: Writes headers to REP-FILE.
    Read Input File: Reads records from INP-FILE.
    Process Records: Validates input, processes records, updates commission data, and generates output records.
    Write Reject Records: Writes rejected records to REJ-FILE.
    Write Output Records: Writes processed records to OUT-FILE.
    Process Report: Processes data for the report.
    Build Report: Builds the report records.
    Write Report: Writes report records to REP-FILE.
    Write Footers: Writes footer records to REP-FILE.
    Close Files: Closes all files.

Program Logic:

    Initialization and File Handling:
        The program opens input (INP-FILE), output (OUT-FILE, REP-FILE), reject (REJ-FILE), and commission (COM-FILE) files.
    Record Processing:
        Reads records from INP-FILE.
        Validates input records for various criteria like date format, currency, and schema matching.
        Rejects invalid records to REJ-FILE.
        Processes valid records, updating commission data (COM-FILE), and generating output records to OUT-FILE.
        Calculates total amounts and transaction counts based on schema and card type.
    Report Generation:
        Builds and writes header records to REP-FILE.
        Processes input records to generate a report, accumulating totals for valid transactions.
        Writes report records to REP-FILE.
        Writes footer records including rejection counts, system date, and time to REP-FILE.
    Error Handling:
        Handles file errors (opening, reading, writing, and closing) by displaying error messages and calling a subroutine (ILBOABN0).
    Commission File Update:
        Reads and updates commission data from COM-FILE based on input records.

Notes:

    The program uses various flags (SW-VALID, SW-INVAL, etc.) to manage validation and processing flow.
    It maintains count and total variables (CN-AMNT-TOT, CN-NO-OF-REC, etc.) for reporting purposes.
    Date validation and processing are done using the WS-DATE-FOR-LINKAGE and COBTEST1 subroutine.
    Commission data is read from and written to COM-FILE, updating commission values based on input records.
    Report records are accumulated and written to REP-FILE.
    The program handles both valid and invalid input records, ensuring proper logging of errors and rejection counts.

This COBOL project provides a structured approach to processing input data, generating output records, and generating a summary report based on specified criteria and business rules. It incorporates error handling and ensures accurate data processing and reporting.
