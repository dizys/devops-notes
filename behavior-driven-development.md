# Behavior Driven Development

## What is BDD & TDD

Behavior-Driven Development (BDD)

- Describes the behavior of the system from the outside in
- Used for Integration / Acceptance Testing

Test Driven Development (TDD)

- Tests the functions of the system from the inside out
- Used for unit testing

### BDD

- **Given** a set of preconditions: Things that need to happen to put the system
  into the state needed to perform the tests
- **When** an event occurs: Things that the user does to interact with the
  system under test
- **Then** some testable outcome is observed: The expected outcome of the
  actions performed by the user

### BDD Tactics

- Apply the "Five Why's" principle to each proposed User Story, so that its
  purpose is clearly related to business outcomes
- Thinking "from the outside in", in other words implement only those behaviors
  which contribute most directly to these business outcomes, so as to minimize
  waste
- Describe behaviors in a single notation which is directly accessible to domain
  experts, testers and developers, so as to improve communication
- Apply these techniques all the way down to the lowest levels of abstraction of
  the software, paying particular attention to the distribution of behavior, so
  that evolution remains cheap

## The 5 Why's

The "5 why's" are a way of continuously asking "why?" over an over until you get
to the core of why something happened.

### Examples of 5 Why's

Q. "Why did the system fail in production?" <br> A. "we found an error condition
that wasn't caught"

Q. "Why didn't we catch this condition?" <br> A. "Because we didn't write a test
case for it"

Q. "Why didn't we write a test case" <br> A. "Because the developer wasn't
trained in TDD"

Q. "Why wasn't the developer trained in TDD? <br> A. "Because we cut the
training budget"

### Conclusion of The 5 Why's: Why did the system fail in production?

Because we cut the training budget and didn't properly train our new developers.

## Expected Benefits of BDD

- BDD offers more precise guidance on organizing the conversation between
  developers, testers and domain experts
- Notations originating in the BDD approach, in particular the given-when-then
  canvas, are closer to everyday language and have a shallower learning curve
  compared to TDD tools
- Tools targeting a BDD approach generally afford the automatic generation of
  technical and end user documentation from BDD "specifications"

## BDD Workflow

- First, the developers, testers and business folks explore the problem domain,
  and collaborate to produce concrete examples that describe the behavior they
  want.
- Next, the team use Behave to run those examples as automated acceptance tests.
- As the team work on the solution, Behave tells you which examples are
  implemented and working, and warns you about the ones that aren’t.
- Before you know it, you have one document that’s both the specification and
  the tests for your software.

## BDD Uses Gherkin Syntax

- **Given**: the purpose of givens is to put the system in a known state before
  the user (or external system) starts interacting with the system (in the When
  steps)
- **When**: each of these steps should describe the key action the user (or
  external system) performs
- **Then**: is used to observe outcomes. The observations should be related to
  the business value/benefit in your feature description
- **And**: is used for continuations. Given this And that... Then this And
  that... etc.

## How behave works

- Behave looks for a folder named features with files that have an extension of
  `.feature`
- It then looks for a folder under that called steps that contains the Python
  code to parse the Gherkin sentences in the feature files.

Note: There is no relationship between feature files and step files. Behave
loads all of the steps regardless of how many files they are contained in

### Loading Test Data

feature file:

```feature
Background:
  Given a set of specific users
    | name      | department |
    | Barry     | Shipping   |
    | Pudey     | Receiving  |
    | Two-Lumps | Receiving  |

Scenario: How many people in departments
  When we count the number of people in each department
  Then we will find two people in "Receiving"
  But we will find one person in "Shipping"
```

step file:

```python
@given('a set of specific users')
def step_impl(context):
  for row in context.table:
    users.append({
      'name': row['name'],
      'department': row['department']
    })
```

### Variable Substitution

- You can use variable substitution to make the steps more generic
- This step can now be used to check for any message in a response
- It’s a good idea to make steps as generic as possible for maximum reuse

```python
@then('I should see "{message}"')
def step_impl(context, message):
    assert message in str(context.resp.text)
```

### Feature Definition

08-Behavior-Driven-Development.pdf: P22

### Environment Setup

Behave has a way to setup all of the tests in one place: `environment.py`

- `before_step(context, step)`, `after_step(context, step)`: These run before
  and after every step. The step passed in is an instance of Step.

- `before_scenario(context, scenario)`, `after_scenario(context, scenario)`:
  These run before and after each scenario is run. The scenario passed in is an
  instance of Scenario.

- `before_feature(context, feature)`, `after_feature(context, feature)`: These
  run before and after each feature file is exercised. The feature passed in is
  an instance of Feature.

- `before_tag(context, tag)`, `after_tag(context, tag)`: These run before and
  after a section tagged with the given name. They are invoked for each tag
  encountered in the order they’re found in the feature file.

- `before_all(context)`, `after_all(context)`: These run before and after the
  whole shooting match.

## Selenium

- Selenium automates browsers. That's it!
- It is a web browser driver to test web sites by interacting with the user
  interface just like a human would
- It supports Firefox, Chrome, Safari, IE, PhantomJS
- This makes it perfect for testing the integration of multiple microservices
  that share a common user interface
