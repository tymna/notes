- embeded - if used only inside contract (internal functions)
	`MyContract`
	`└── contains MathLib.max code`
- separate deployment - shared across contracts (public and external functions)
	`MathLib
    `↑
    `│ DELEGATECALL
    `│
    `MyContract
	    - delegatecall - library's code in context of MyContract