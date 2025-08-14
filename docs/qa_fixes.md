Problem: 
`UserResponse` was missing required fields (`last_name`, `created_at`, etc.), causing schema validation failures and inconsistent API responses.
Reproduction: 
- Call any endpoint that returns `UserResponse` (user detail or list).  
- Observe `last_name`/`created_at` missing from payload.  
- Schema tests fail for `UserResponse`.

Fix:
Updated `user_schemas.py` so `UserResponse` includes all required fields and matches the API contract and DB model.
