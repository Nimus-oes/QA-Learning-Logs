# Crypto.com-QA-Takehome-Test-Project
 Project journey and the final output

## Week 1
*November 27th, 2023 - December 3rd, 2023*

Embarking on my journey towards becoming a QA automation engineer, I spent the first week for laying a solid foundation. I aimed to gain a comprehensive understanding of QA automation by following along the introductory QA courses, before proceeding with the take-home test. 

### Key Learnings:  
- **Test Levels**: Grasped the concept of three levels of tests - Unit, Service, and UI tests
- **BDD Understanding**: Acquired insights into Behavior Driven Development (BDD) and its application in the QA process.  
- **Environment Configuration**: Explored the environment for QA automation, including the configuration of a virtual environment. Installed and configured tools such as Selenium, Chromedriver, Behave, pytest, and pytest-bdd.  
- **Web Element Locators**: Delved into web element locators, focusing on CSS selectors and XPath.
- **BDD Tools**: Understood the purposes and use cases of Selenium and pytest-bdd in QA automation
### Learning Resources:  
- [Setting a Foundation for Successful Test Automation](https://testautomationu.applitools.com/setting-a-foundation-for-successful-test-automation/) on Test Automation University
- [Introduction to Pytest](https://testautomationu.applitools.com/pytest-tutorial/) on Test Automation University
- [Web Element Locator Strategies](https://testautomationu.applitools.com/web-element-locator-strategies/) on Test Automation University
- [Selenium WebDriver with Python](https://testautomationu.applitools.com/selenium-webdriver-python-tutorial/) on Test Automation University
- [Behavior Driven Python with pytest-bdd](https://testautomationu.applitools.com/behavior-driven-python-with-pytest-bdd/) on Test Automation University
### Plans for Next Week  
- To dive deeper into the implementation of web element locators with Selenium  
- To explore the functionalities and applications of pytest-bdd in QA automation process


## Week 2
*December 3rd, 2023 - December 10th, 2023*

This week was a bit challenging as I had to fight the flu with my completely blocked nostrils. Despite the health condition, I managed to revisit and dive deeper into some of the topics covered last week.

### Key Learnings: 
- **Virtual Environment Optimization**: Discovered that the default virtualenv provided by PyCharm isn't the best fit for pytest, leading to module missing errors. Switching to venv resolved these issues effectively.
- **Exception Handling in pytest**: Learned how to use `pytest.raises` as a context manager in pytest for error handling instead of try-except block
- **Parameterizing a Test**: Learned to use `pytest.mark.parametrize` decorator for equivalence classes to parameterize inputs across multiple test functions
- **3-step Pattern of Functional Test**: Understood the Arrange-Act-Assert pattern of the functional test
- **pytest Fixture**: Learned that fixtures are used to inject dependency into test cases, creating assets required during the Arrange step in the Arrange-Act-Assert pattern
- **pytest Test Filtering Options**: Discovered the various ways to filter tests cases in pytest by using directory/module path or `-k` command in command line and markers as name tags

### Learning Resources:
- [Introduction to Pytest](https://testautomationu.applitools.com/pytest-tutorial/) on Test Automation University

### Plans for Next Week
- To dive deeper into the implementation of web element locators with Selenium  
- To explore the functionalities and applications of pytest-bdd in QA automation process


## Week 3
*December 11th, 2023 - December 17th, 2023*

This week my focus shifted towards applying theoretical knowledge of web element locators and Selenium WebDriver into practical test cases. As I delved into the crypto.com/exchange/markets webpage using Selenium, I encountered a significant roadblock hindering proper testing of the markets page. 

### Challenges: 
- **Redirection Issue**: Whenever attempting to access the **crypto.com/exchange/markets** page with Selenium WebDriver, the page is unexpectedly redirected to **crypto.com/exchange**
- **Page Loading Issue**: Even accessing the **crypto.com/exchange** has a lot of hurdles - the page loading was working randomly, only 2 out of 10 times approximately
- **Failed Redirects**: Even when the **crypto.com/exchange** page is fully loaded, it resisted redirection to the markets page after a button click, with the URL still remains as **crypto.com/exchange**

### Analysis:
- **Issue Origin**: To isolate the problem, I replicated the code structure on other websites like Binance, where it worked seamlessly. The issue seemed tied to the Crypto.com/exchange website itself rather than my Python and Selenium configurations.
- **Attempted Approaches**: Assuming it could be related to the anti-bot system of Crypto.com exchange, I tested with headless mode, custom Chrome profile, debugger chrome, and user-agent but none of them proved to be working. It occurred to me that it might not be the anti-bot system given the crypto.com/exchange website can be loaded even if it's very random and rare. Then the remaining issue was the network.
- **The Solution**: crypto.com/exchange/markets page was fully loaded when using a VPN in a different region. The reason markets page isn't loaded appears to be the [geo-restriction](https://help.crypto.com/en/articles/6320975-spot-trading-geo-restrictions) imposed by Crypto.com. 

### Alternative Plan for the Assignments
- Given the challenges, I opted for France as my test location for the assignments. It proved to be a region with smoother access to page features, devoid of disclaimers that could disrupt the testing flow.

### Plans for Next Week
- To explore the functionalities and applications of pytest-bdd in QA automation process
- To proceed with the first assignment applying all the knowledge I gained so far


## Week 4 & 5
*December 18th, 2023 - December 29th, 2023* 

Christmas and new year holidays are just around the corner, but I kept persevering.
These past two weeks were dedicated to progressing through the first UI test assignment. I've encountered countless errors and that made me learn so much more that I did with lectures and sample test.

### Challenges: 
- **ElementClickInterceptedException**: Most of the time, the error was about Element Click Intercepted Exception. After some intensive search and testing, I found the issue is mainly fixable by waiting for the element to be interactable or moving the element to the viewport. 
> **Solution**:
> 1. Explicitly wait for the element to be interactable
> 2. Scroll the element into viewport
> 3. Try different types of click method
- **Wait not working properly**: Implicit waits, while seemingly straightforward, didn't consistently perform as expected, particularly during page navigation or dynamic content loading.
> **Solution**:
> 1. Set explicit waits to each element where applicable
> 2. Set hard sleep when necessary as a practical workaround
- **Locating an SVG element with XPath**: Even though it was possible to locate an SVG element with XPath in the browser inspection, same Xpath didn't work with Selenium. 
> **Solution**: Use `name()` or `local-name()` method
- **Markets page not accessible with Firefox**: Markets page remains inaccessible on Firefox even with a VPN
> **Solution**: No solution found yet. Decided not to support Firefox for the test at this stage.
- **Dropdown menu inactive**: 'Categories' dropdown menu is unresponsive to Selenium actions, unlike other dropdowns in the page.
> **Solution**: No solution found yet. Decided not to support this test case at this stage.
  

### Plans for Next Week
- To handle inputs with json
- To make sure the test runs smoothly in both desktop and mobile environment
- To make it available to set window size with commands when running tests  



## Week 6 & 7
*December 30th, 2023 - January 8th, 2024*  

During these two weeks, I focused on increasing the coverage of the test suite, so that it tests both desktop and mobile environment smoothly.
Additionally, I have tried to improve the code quality by removing the duplicates and redundancy.

### Key Achievements  
- Created a new helper method in the test file so that it handles repetitive shared steps across all test cases and removed the old ones in the page object models.
- Added markers for increased modularity
- Installed pytest-html and tested populating the report for each test
- Tested parallel testing with pytest-xdist
- Completed project setup guide with ReadMe

### Challenges 
- **Scroll action discrepancy between mobile and desktop**: When scrolling up to the 'Favorites' navigation tab after clicking the start button to add the pair to the favorites, the scroll suddenly stops in the middle in the mobile environment. No issue found with the desktop version.
> **Solution**: Set hard sleep so the scroll can be completed
- **Markets page inaccessible in headless mode**: The page remains inaccessible in headless mode even with a VPN 
> **Solution**: No solution found yet. Decided not to support the headless mode at this stage.  
- **Spot page inaccessible with footer navigation**: When 'Spot' is clicked under the footer 'Trade' navigation menu, new window opens, and it redirects to crypto.com/exchange page.
> **Solution**: No solution found yet.  

### Room for Improvements 
- The test suite can be improved to take spot trading pairs as varying inputs so that it can test any pair provided, making the suite more compatible and reusable.  
> - All navigation menus under 'Spot' market can be tested (Favorites, All, USD, USDT, BTC, CRO, EUR)
> - The recommended item banners under 'Spot' market can also be tested 

#
## Week 8
*January 9th, 2024 - January 15th, 2024*  

Now that the basic version of the UI test is completed, it's time to transition to the next assignment—the API test. While I have a foundational understanding of API interactions and can write the test code using pytest, just like in the UI test, I've chosen to push my boundaries a bit further by incorporating the pytest-bdd framework this time.

Before diving into the test development, I took a course to familiarize myself with the pytest-bdd framework, ensuring a solid grasp of its functionalities and best practices. 

### Key Learnings  
- **The Structures of Feature and Steps**: Learned how to write feature file with Scenarios in Gherkin language and write steps file with each step for the corresponding scenario
- **Input Parameterization**: Learned how to parse the inputs and parameterize them with parse function and Scenario Outline
- **Dealing with Multiple Scenarios**: Understood that multiple scenarios can share certain steps, removing the code repetition
- **Test Filtering with Tags**: Learned that pytest-bdd tags can be used just like marks in pytest to filter the tests  

### Learning Resources  
- [Behavior Driven Python with pytest-bdd](https://testautomationu.applitools.com/behavior-driven-python-with-pytest-bdd/) on Test Automation University