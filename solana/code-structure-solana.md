
src/                                                                                                         
  | ── **lib.rs**         entry point (+functions)                                               
  │   ├── init()                                                              
  │   └── update()        
  │                                                                                                            
  | ── **state.rs**            data                     
  │   └── struct Oracle { owner, price }                                                                       
  │                                                                                                            
  └── instructions/                      
      ├── mod.rs                                                          
      ├── **init.rs**         # Init struct (accounts) + init fn (logic)                                           
      └── **update.rs**       # Update struct (accounts) + update fn (logic)     