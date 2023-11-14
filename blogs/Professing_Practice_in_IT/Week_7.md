# Week 7 - Test Management
## Lecture

Testing phases:
- Requirement phase - Requirements review
- Planning phase - Test planning
- Design phase - Test design
- Development phase - Unit testing
- Integration phase - Integration testing
- System phase - System testing
- Acceptance phase - User acceptance testing
- Release phase - Deployment testing
- Maintenance phase - Regression testing

### Testing During Development

Done by development team.

#### Component Test (Unit Test)

- To ensure that each component behaves 'correctly'
- Uses white-box testing

#### Integration Test

- To test interaction between related components
- Focuses on interfaces between components
- Top-down integration testing
  - Advantage:
    - Early validation of system functionality
    - Supports high-level design
  - Drawback
    - Dependencies on incomplete lower-level components
    - Delayed system testing
- Bottom-up integration testing
  - Advantage:
    - Early detection of critical component issues
    - Supports parallel development
- Drawbacks
    - May require extensive use of stubs and drivers
    - Complex coordination
  
#### System Test
- To ensure that the user requirements have been met
- Focuses on usual business processes, and normal workflow

### Functional and Non-functional Requirements

#### Functional Requirements
What the system should do.

Specifies features and use cases.

#### Non-functional Requirements
Performance, security, usability, scalability.

Specifies performance goals, constraints, and limits.

### Testing During Deployment

#### Performance Test (Load Test)
- To test system performance under maximum expected load.
- Simulates key processes under maximum load

#### Soak Test and Stress Test

- To ensure that system is stable over extended period.
- Load increased until system fails. Checks effects of over-load.
- Identify breaking points and recovery behavior.
- Push system beyond its limits, observe failures and recovery.


#### Acceptance Test
Conduct by the end-users (customers).

- Compares system functionality against agreed-on user requirements.
- Carried out by client using scenarios, supervised by developer.


### Case Study
#### ESA
The same software is successful in Ariane 4 but fail in Ariane 5 rocket.

Fitting 64-bit Inertial Reference System to 16-bit. 

#### Nectar Card Fiasco
Customer loyalty scheme.

At deadline, millions users found they were locked out. (Too much access.)

Performance testing had not anticipated the level of user load.

#### TESCO

Detailed test plan, well test management.
- Capacity model
- Usage model
- Test database
- To include sock and stress testing 

#### Mobile MedSoft QA
Challenges:
- Application complexity
- Environment Complexity
- Agile development

Solutions:
- Full regression and test management 
- Automated testing
- Usability testing
- Performance testing
- agile testing collaboration


### Test Data and Test Scenarios

Determine target load


## Reading

### [The Different Types of Software Testing](https://www.atlassian.com/continuous-delivery/software-testing/types-of-software-testing)

#### Manual vs Automated Testing
Manual testing is more expensive.

Automated testing is more robust and reliable than manual tests. However, the quality of automated tests depends on how well the test scripts have been written.

#### The Different Types of Tests
- Unit tests
- Integration tests
- Functional tests
  - Focus on the business requirements of an application
  - Verify the output of an action
- End-to-end tests
  - Verify various user flows work as expected.
- Acceptance tests
- Performance tests
- Smoke tests
  - Basic tests that check the basic functionality of an application.

#### Note
It's important to test that users can actually use an application, it is equally important to test that an application doesn't break when bad data or unexpected actions are performed.

### [QA Roles and Responsibilities: Who Do You Need on Your Software Testing Team?](https://u-tor.com/topic/qa-roles-and-responsibilities)

