## Submission: 
1. Submission is in pairs, but it's better for practice if you start alone.
2. Grades: code part: 70%, questions: 30%.
3. Your submitted git repo should be *private*, please make barashd@post.bgu.ac.il a collaborator.
5. Deadline: 13/06/2023, end of day.
6. Additionally, solve the questions in [will be filled later](https://www.notexists.bgu.ac.il/).
7. To submit, fill in repository details in the following Moodle [will be filled later].(https://moodle.bgu.ac.il/moodle/mod/questionnaire/view.php?id=2472729).
8. in Atlas: Set the allowed IP addresses to 'all' (0.0.0.0).
9. Download the final submitted version to a new dir and make sure it installs and runs correctly, preferably on a fresh machine.

## Goals
1. enable all users, regardless if they have GitHub, to log in.
2. support user management, for features that we might want in the future: friends, groups, private messages, etc.
3. understanding how authorization works hands-on.
4. practice Test-driven development.

## Task
This task's main goal is to add profiles to our posts website; the task is split to:
1. user management: replace nextAuth with token auth from [fullstackopen part 4](https://fullstackopen.com/en/part4/user_administration).
3. front end: profile page, sign up page, sign in page.
4. testing: you have to submit 10 backend tests (See tips for TDD below)

## Implementation - backend

### Library
2. Remove the next-auth lib from the project. (** See what was added to support it here: https://next-auth.js.org/)

### Database
1. We need to store the password hashes. you're free to design the database schema as you wish. At least two possible options (you can come up with more):
    1. the least changes would be to use the existing schemas to store passwords as well.
    2. if you prefer working with Mongo, and be aligned with FSO examples, you can change your code to store users and their passwords there.
    
### API routes
1. implement a route that adds a new user.
2. implement a login of an existing user.

### middleware
1. Implement a middleware to verify a user is logged in, before reaching the post/publish/profile API endpoints.

## Implementation - Front

### Front-end components
1. create a "sign in" and "log in" page for unauthenticated users. They can still see the public feed. since we remove the next-auth lib, those will be the only available login options from now on.
2. create a profile page for authenticated users. They can see the link to it on the main page of the app.
    1. Clicking on it, shows a page with the details of the current user.
3. each user must have a username, password, email, and name. optional input: age, profession, and address. the email is the unique identifier of the user. 
4. you should verify the inputs and send status/error codes (200- ok, 204- success and no content, 201- created, 400 bad request, 403-forbidden, 404- doesn't exist, 500- internal server error, and others) from the backend. For example:
    1. A user cannot create an existing other user's email address: this will return a bad request code.
    2. A user must enter an email, it can be verified at the front end.
5. for simplicity, the username, password, and email cannot be changed after user creation.
6. for this homework, we don't support user deletion.


### Test Driven Development ("Clean Code"/ Robert C. Martin, Chapter 9, unit tests)
1. You're invited to take this exercise as an opportunity to practice TDD, which will make you a better programmer.
2. The three laws of TDD:
    1. You may not write production code until you have written a failing unit test.
    2. You may not write more of a unit test than is sufﬁcient to fail, and not compiling is failing.
    3. You may not write more production code than is sufﬁcient to pass the currently failing test.
3. building a domain-speciﬁc language for your tests. Rather than using the APIs that programmers use to manipulate the system, build up a set of functions and utilities that make use of those APIs and that make the tests more convenient to write and easier to read. For example:
    1. nonExistingId() will return a non-existing database id, instead of writing the actual code to generate that id.
4. One comfortable way to write a single test is the "given-when-then" convention:
    1. given that a user is in the database, and a correct auth request is made, then success is expected.
    2. given an existing post id, a delete request is sent to /api/post/:id, then I expect the post to be returned.
    3. A matter of taste: if "then" expects more than one result, separate each one to a different test, (at the cost of code duplication).
        1. You can use tests API to reduce code duplication: with mutual beforeEach, afterEach, mutual 




### Bonus: up to 10 points ("magen" for the exercises) for extra features:
1. Let the user add a profile picture. Save it to Cloudinary.
2. Make the photo editable with a click, at the profile page.
3. Wherever there's a post shown, add the profile picture of the author.

## Prerequisites

### Client side: uploading a video file:
1. Read about testing, user administration, and authentication at https://fullstackopen.com/en/part4/.
2. Read about bcrypt format: https://en.wikipedia.org/wiki/Bcrypt and https://stackoverflow.com/questions/32918460/why-is-the-hash-generated-by-bcrypt-non-deterministic.
3. Read about JSON Web Token: https://jwt.io/introduction.



### Tips:
1. Try the [vscode debugger for nextjs.](https://nextjs.org/docs/pages/building-your-application/configuring/debugging), it's easy to install and use most of the time, but sometimes the breakpoints don't work.
2. Use a 

### Github 
Like before, Hw2 will be submitted via Github: fill the group in the Moodle link.

### Grading process:
1. Clone your submitted repo. 
2. Run the starter scripts.
3. Performance test against a large, no video database from hw1.
4. Manually test the video feature and any extra features.

### Getting started- 
See the previous homework instructions.

## Good luck!



