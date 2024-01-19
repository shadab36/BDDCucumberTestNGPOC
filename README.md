Selenium-Cucumber-Java
This repository contains a collection of sample projects and libraries that demonstrate how to use `selenium-cucumber-java`, a BDD (Behavior-Driven Development) framework with Cucumber (v 3.0.0) and Java. The projects showcase automation script development and utilize various reporters such as Allure, HTML, and JSON. Additionally, it offers the ability to capture screenshots for tests and generate error shots for failed test cases.

Installation & Prerequisites
1. JDK 1.8+ (Ensure that the Java class path is properly set)
2. Maven (Ensure that the .m2 class path is properly set)
3. Eclipse IDE
4. Required Eclipse Plugins:
   - Maven
   - Cucumber
5. Browser driver (Ensure that you have the appropriate browser driver for your desired browser and that the class path is correctly configured)

Framework Setup
To set up the framework, you can either fork or clone the repository from [here](https://github.com/amiya-pattnaik/selenium-cucumber-java), or download the ZIP file and set it up in your local workspace.

Running Sample Tests
Access the CLI of your operating system (e.g., iTerm for macOS or PowerShell for Windows) and navigate to the project directory. Then, run the following command to execute the features: `mvn clean test`. 
By default, this command will invoke the Firefox browser and execute the tests.
- To run features on a specific browser, use the command: `mvn test "-Dbrowser=browser_name"`. Replace `browser_name` with one of the following options: Firefox, Chrome, Safari, etc. Ensure that the browser's driver files are present and specified in the system variables.
// Need to find out if Internet Explorer is supported or this should be updated to Edge, then update details around IE to Edge
Please note that browser drivers are not included as part of this framework. The reason for this is that the version of Selenium browser drivers varies based on the browser version you are using, as well as the Selenium server version.

- To run a specific feature file among multiple feature files, use the command: `mvn test -Dcucumber.options="classpath:features/my_first.feature"`.

Reporters
Once you have run your tests, you can generate various types of reports. This `selenium-cucumber-java` framework utilizes different test reporters to communicate pass/failure information.

Reporting
Allure Report
To generate an Allure report, you can use one of the following commands:
- `mvn allure:serve`: This command generates the report in the temp folder and opens a web server with the results in your default browser. 
- `mvn allure:report`: This command generates the report in the `target/site/allure-maven/index.html` directory, allowing you to view it locally.

HTML Report
To generate an HTML report, use the following command: `mvn test -Dcucumber.options="--plugin html:target/result.html"`. 
This command generates an HTML report, and you can find it at `target/result.html`.

JSON Report
To generate a JSON report, use the following command: `mvn test -Dcucumber.options="--plugin json:target/result.json"`. 
This command generates a JSON report, and you can find it at `target/result.json`.

Extent Spark Reports
The framework utilizes the [Spark Reports Framework] (http://www.extentreports.com/docs/versions/4/java/spark-reporter.html) to generate HTML test reports. 

BDD Automation with Cucumber-Java and Page Objects
In this repository, we encourage the use of Behaviour-Driven Development (BDD) with Cucumber and Java to develop automation scripts. We provide predefined Step Definitions packaged under `/steps/Commonsteps.java` to help you accelerate your automation development. These Step Definitions support commonly used helper methods and can be customized according to your needs.
Tests are written in the Cucumber framework using the Gherkin syntax. If you're new to Gherkin and Cucumber, you can find more information at [cucumber.io/docs/reference](https://cucumber.io/docs/reference). A typical test will have a structure similar to this:

gherkin
Feature: Performing a Google Search
    As a user on the Google search page
    I want to search for Selenium-Webdriver
    Because I want to learn more about it
    Background:
        Given I am on the search page
    Scenario: Performing a search operation
        When I enter "Selenium Webdriver" into the search box
        And I click the search button
        Then I should see a list of search results
    Scenario Outline: Performing a search operation with test data from a data table
        When I enter <searchItem> into the search box
        And I click the search button
        Then I should see a list of search results
        Examples:
        | searchItem         |
        | "Selenium Webdriver" |

The Page Object Design Pattern
To better organize your test code and make it more maintainable, we recommend using the Page Object Design Pattern. With this pattern, the UI elements of your web application are modeled as objects within the test code. This approach reduces code duplication and allows easy updates if the UI changes. Writing and maintaining test automation can be challenging, especially when it comes to keeping selectors (classes, IDs, or XPath, etc.) up to date with the latest code changes. The Page Object pattern provides a solution by centralizing these selectors in separate <pagename>.java files, where you can manage them along with the associated methods.
By using the Page Object pattern, your test files will only call the test methods, while the selectors and reusable methods reside in the corresponding Page Objects. This approach helps maintain a separation of concerns and ensures that when a test fails, it fails on an individual step. If a selector becomes invalid, updating it in the Page Object file can fix multiple failing tests that rely on the same selector.
Implementing the Page Object pattern promotes maintainable and scalable test automation code, making it easier to adapt to UI changes and keep your code DRY (Don't Repeat Yourself).

Contribution
We welcome and encourage contributions from the community to make this project even better! If you have ideas, bug fixes, or new features to contribute, follow the steps below:

1. Fork the project repository to your own GitHub account.
2. Create a new branch for your changes and switch to it.
3. Make the necessary changes, additions, or bug fixes in your branch.
4. Write clear and concise commit messages to explain the purpose of each change.
5. If your contribution introduces new functionality, consider adding tests to ensure its robustness.
6. Once your changes are ready, submit a pull request (PR) to the original repository.
7. In the PR description, provide a detailed explanation of the changes you made, including any relevant context or background information.
8. The project maintainers will review your PR, provide feedback, and collaborate with you to refine the changes if needed.
9. Once approved, your contribution will be merged into the main project.
10. Celebrate your successful contribution! 🎉

