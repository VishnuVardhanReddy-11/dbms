```mermaid
erDiagram
    BOOK_DETAILS {
        string ISBN PK
        string Title
        string Author
        string Publisher
        string Category
        int Publication_Year
    }

    BOOK {
        int Book_ID PK
        string ISBN FK
        string Shelf_No
        string Status
    }

    BORROWER {
        int Borrower_ID PK
        string Name
        string Email
        string Phone_No
        string Address
        date Membership_Date
        string Membership_Type
    }

    LIBRARIAN_LOGIN {
        string Username PK
        string Password
    }

    LIBRARIAN {
        int Librarian_ID PK
        string Name
        string Email
        string Phone_No
        string Shift_Timing
        string Username FK
    }

    TRANSACTION {
        int Transaction_ID PK
        int Book_ID FK
        int Borrower_ID FK
        int Issued_By FK
        date Issue_Date
        date Due_Date
        date Return_Date
        string Status
    }

    FINE {
        int Transaction_ID PK, FK
        decimal Fine_Amount
        string Payment_Status
        date Payment_Date
    }

    %% Relationships
    BOOK_DETAILS ||--o{ BOOK : "1 — N"
    BOOK ||--o{ TRANSACTION : "1 — N"
    BORROWER ||--o{ TRANSACTION : "1 — N"
    LIBRARIAN ||--o{ TRANSACTION : "1 — N"
    LIBRARIAN_LOGIN ||--|| LIBRARIAN : "1 — 1"
    TRANSACTION ||--|| FINE : "1 — 1"
