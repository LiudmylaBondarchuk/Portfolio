# Jira Cloud API Tests

Test suite for Jira Cloud API, focusing on end-to-end validation of the project management ecosystem in the organization.

## Execution Metrics
- **117 integration tests** - validation of complete business scenarios
- **98 API requests** - coverage of key system functionalities
- **1m 37s** - complete validation execution time
- **98.3% Success Rate** - production environment level stability

## Quick Access
* [📥 Download Collection](https://github.com/LiudmylaBondarchuk/Portfolio/blob/master/api-tests/jira-tests/collection/Jira%20Cloud%20API%20Tests.postman_collection.json)
* [📝 Instructions to Run Collection](https://github.com/LiudmylaBondarchuk/Portfolio/blob/master/api-tests/jira-tests/collection/README.md)
* [📄 Test Results](https://github.com/LiudmylaBondarchuk/Portfolio/blob/master/api-tests/jira-tests/collection/results/Jira%20Cloud%20API%20Tests.postman_test_run.json)
* [🐞Bug Report](https://github.com/LiudmylaBondarchuk/Portfolio/blob/master/api-tests/jira-tests/collection/results/bug-report/01_bug_report_jira_cloud_api.md)

## Testing Method
### End-to-End Integration Testing
- **Complete business workflows** - from project creation through tasks to cleanup
- **Bulk data generation** - automatic creation of related test structures in loops
- **Cross-module dependencies** - integrity testing between system components
- **Single comprehensive test per request** - one test checks multiple aspects simultaneously

## Testing Spectrum

### Core Functionality
- **Projects Lifecycle** - creation, modification, search, deletion with business rules
- **Issue Hierarchy** - Epic → Task → Subtask with integrity control and type conversions
- **JQL Filters** - creation, modification, and filter search
- **Bulk Operations** - mass creation of projects, epics, tasks, and subtasks

### Negative Scenarios
- **Data Validation** - invalid characters, lengths, date formats, key duplicates
- **Business Rules** - hierarchy violations, cyclic dependencies, unauthorized access
- **Security Boundaries** - malformed requests, wrong content types, CloudFront blocks

### Edge Cases and Boundary Testing
- **Extreme date values** - testing year 2048, February 29 in non-leap year
- **Maximum lengths** - 32,766 characters in descriptions, 255 characters in titles, 1000+ labels
- **Case sensitivity** - testing case sensitivity in labels
- **Hierarchy conversions** - Epic↔Task↔Subtask with integrity validation

### International Character Support
- **Unicode testing** - Cyrillic (русский), Chinese (中文), Arabic (العربية), Polish (ąęśćżółń), German (äöüß)
- **Emoji support** - 🚀📈🔧 in names and descriptions
- **Special characters** - @#$%^&*()_+-=[]{}|";':<>?

## Detected API Defects

### System Bugs
1. **Silent Date Modification** - API automatically modifies future dates (2048→other) without notification
2. **Orphaned Subtasks** - Task→Epic conversion may leave unlinked subtasks

## Bug Report Attachments

### [Bug #1: Silent Modification of Future Dates](https://github.com/LiudmylaBondarchuk/Portfolio/blob/master/api-tests/jira-tests/collection/results/bug-report/01_bug_report_jira_cloud_api.md#bug-1-silent-modification-of-future-dates)

### [Bug #2: Orphaned Subtasks After Task-to-Epic Conversion] (https://github.com/LiudmylaBondarchuk/Portfolio/blob/master/api-tests/jira-tests/collection/results/bug-report/01_bug_report_jira_cloud_api.md#bug-2-orphaned-subtasks-after-task-to-epic-conversion)

## Technologies
- **Jira Cloud REST API v3** - latest version
- **Postman JavaScript** - advanced pre/post-request scripts with loops and logic

## Business Value

### QA Teams:
- Ready framework for testing Jira integration in corporate environment
- Automatic regression and incompatibility detection
- Testing patterns for systems with complex dependencies

### Development Teams:
- Integration validation before deployment
- Production problem debugging scenarios
- Performance benchmarking for API calls

### Business Teams:
- Compliance verification with organizational business processes
- Functional requirements coverage documentation
- Risk mitigation for critical corporate integrations
