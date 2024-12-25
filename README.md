# PostmanAPITestingFramework
This framework tests open-source API's

In this testing framework - I have tested API's and automated the validations required for tests
This framework uses - 
1) Javascript for programming
2) NewMan for CLI integration
3) Data-Driven testing when required
4) Different env can be integrated depending upon use case (As of now testd with QA env)
5) Pre-request script is setup for one of API request
6) Tests are used for validation of API response received
7) Query_params are set in variables
8) Examples are added for each API request to make it easier for review and setup
9) HTML reports are generated

![napkin-selection (10)](https://github.com/user-attachments/assets/06471db4-c847-42a8-85be-04ec852dbb7b)


Project Structure:

The framework is organized with the following files:

- README.md: This is the project's documentation. It describes the framework's purpose, features, technologies used, and how to use it.
- test_data_Create_User.csv: This is a CSV (Comma Separated Values) file used for data-driven testing. It contains multiple sets of data that will be used as input for the CreateUser API request.
- Users.postman_collection.json: This is the core of the framework. It's a JSON file containing the Postman collection. This file defines all the API requests, tests, pre-request scripts, and other configurations.
- Users.postman_test_run.json: This file contains the results of a test run using Newman. It shows the test results, including pass/fail counts, response times, and other details.
- newManCommands.txt: This file contains instructions and commands for setting up and using Newman, the command-line tool for running Postman collections.
- QA.postman_environment.json: This is a Postman environment file. It contains environment-specific variables, such as the base URL of the API.

![napkin-selection (6)](https://github.com/user-attachments/assets/dbe31e03-027a-4b84-96bc-9a312dea7252)

Core Entities within Users.postman_collection.json:

- info: Contains metadata about the collection, such as its name, ID, and schema.

- item: This is an array of API requests (also called "items"). Each item represents a specific API endpoint and its associated tests and configurations.

- name: The name of the API request (e.g., "GetAllUsers", "CreateUser").

- event: An array of events that can be triggered at different stages of the request lifecycle.

- listen: Specifies when the script should run (e.g., "test" for after the response is received, "prerequest" for before the request is sent).

- script: Contains the JavaScript code to be executed.

- exec: An array of strings, each representing a line of JavaScript code.
- type: The script type (usually "text/javascript").
- request: Defines the API request itself.

- method: The HTTP method (e.g., "GET", "POST", "PUT").

- header: An array of HTTP headers.

- body: The request body (for POST, PUT, etc.).

- mode: The format of the body (e.g., "raw", "formdata").
- raw: The raw body content.
- options: Options for the body, such as the language ("json").
- url: The API endpoint URL.

- raw: The complete URL.
- host: The base URL.
- path: The path segments.
- query: Query parameters.
- response: Contains example responses for the request. These are for documentation and preview purposes within Postman. They are not used during automated test execution by Newman.

- event (Collection-level): Similar to item-level events, but these apply to the entire collection.

- variable: An array of collection-level variables. These variables can be used in requests, scripts, and tests.
  

  ![napkin-selection (7)](https://github.com/user-attachments/assets/8244502f-7024-4d21-abe9-c2f0c3ba9cb9)

  Key Concepts and Technologies:

- Postman: A popular API development and testing tool. It provides a graphical interface for creating and sending HTTP requests, as well as writing tests and managing collections.
- Newman: A command-line tool for running Postman collections. It allows you to automate API tests as part of a CI/CD pipeline.
- JavaScript: The scripting language used in Postman tests and pre-request scripts.
- Data-Driven Testing: A testing technique where test data is stored in a separate file (like the CSV file here) and used to run the same test multiple times with different inputs.
- Pre-request Scripts: JavaScript code that runs before a request is sent. These are used for tasks like setting variables, generating authentication tokens, or modifying the request.
- Tests (Post-request scripts): JavaScript code that runs after a response is received. These are used to validate the response status code, body content, headers, and other aspects of the response.
- Collection Variables: Variables that are defined at the collection level and can be accessed by all requests and scripts within the collection.
- Environment Variables: Variables that are defined in an environment file and can be used to configure tests for different environments (e.g., development, testing, production).

  ![napkin-selection (8)](https://github.com/user-attachments/assets/bc31e49f-50f2-4757-b7e5-d9aeb96eef72)

Workflow:

- The API requests, tests, and configurations are defined in the Users.postman_collection.json file using Postman.

- Test data is stored in test_data_Create_User.csv.

- Environment-specific variables are stored in QA.postman_environment.json.

- Newman is used to run the collection from the command line, using the following command (as shown in newManCommands.txt):

newman run Users.postman_collection.json -d test_data_Create_User.csv -e QA.postman_environment.json

- Newman executes the requests, runs the tests, and generates a report (which can be in various formats, including HTML). The Users.postman_test_run.json provides an example of the output.

  ![napkin-selection (9)](https://github.com/user-attachments/assets/ed79423d-2d0b-4172-b95c-580a20d5282f)
