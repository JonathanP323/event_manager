# Event Manager 

[QA Issue 1](https://github.com/JonathanP323/event_manager/issues/1)

[QA Issue 2](https://github.com/JonathanP323/event_manager/issues/2)

[QA Issue 3](https://github.com/JonathanP323/event_manager/issues/3)

[QA Issue 4](https://github.com/JonathanP323/event_manager/issues/4)

[QA Issue 5](https://github.com/JonathanP323/event_manager/issues/5)



# Reflection

###        When doing this assignment, great emphasis was given to the alignment of the backend API schemas and the real database models as well as the seamless interaction between different parts of the system. Among the main problems that were dealt with lay the inconsistency between userResponse schema and the information being sent back by API. Not having the mandatory fields such as last_name and created_at failed not only schema validation, but also made the API contract with the front end to have the missing field. Through an update of UserResponse to complete the database model exactly including all the attributes that are required, the system is now capable of providing consistent, predictable, and complete responses. The integration of the persistence layer and the API layer have also become stricter, hence decreasing the threat of data mismatch in production. It strengthened the need to have stringent schema validation as an insurance against silent data loss or incomplete payloads. 
###        Requirements to make request validation better, especially in the case of authentication, became another improvement area. The LoginRequest schema did not initially have valid strong validation rules so malformed or otherwise incomplete data had the potential to work its way through. This was a threat to unreliable login behavior where some invalid requests may succeed and at random others might fail. With our explicit field definitions and proper data types being enforced the login requests no longer need to be attempted before being handed off to the authentication logic, being validated first. Not only does this enhance security, it also makes the developers experience smoother as earlier errors are caught during the parsing phase of the request. Similarly, the token generation process was embellished to manage the UserRole enums properly. Before, we got errors in serialization when passing an enum directly into create_access_token(). Now encoding these first to their string value before encoding fixed this, so that tokens can then store role information reliably without compromising JWT encoding.
###        Other minor bugs but no less significant were those that were a correction to stability issues at run-time and the visibility of errors. The failure to import an Enum in the user models led to the execution failing in cases where the roles had to be used. This was a fairly straightforward correction, however it served as a reminder of the kinds of issues that a small issue during imports can cause. Of utmost importance, the SMTP silences without email notification system were identified and resolved. Having the send logic in a wrapped try-except block and logging errors allows the system to fail gracefully when there is a hiccup in email delivery which no longer causes the system to stall when creating a user or running tests. This enhances durability and sustainability, so that operational problems will not translate into the collapse of the entire system. On the whole, this assignment helped improve the schema matching, validation rigor and error handling, as well as robust interface integration of all the back end pillars key facets in producing a consistent production ready API.
