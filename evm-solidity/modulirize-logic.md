Need to modularize logic?
│
├── Logic operates on some State/data
│       → Library
│
├── Need shared storage + modifiers / hooks / overridable behavior
│       → Inheritance
│
└── Logic is small and tightly coupled to one contract
        → Internal function