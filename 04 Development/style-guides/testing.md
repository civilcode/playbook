# Testing Style Guide
What and where to test:

* Acceptance tests `features` (Cucumber):
  * Separate feature file for each feature set
  * Domain API
  * UI
  * At least one scenario for error handling (both domain & UI)
* Model specs `spec/models/:
  * logic
  * validations
  * not the associations
* Controller specs `spec/controller`
  * no controller specs, unless there is something awkward to test.
* Request specs `spec/requests/`
  * CRUD'ing look up tables (i.e. not business operations)
  * following the notes on the "Web World" for how to structure tests
  * example: [EventType Request Spec](https://github.com/airslie/renalwarev2/blob/master/spec/requests/events/event_types_spec.rb)

## Notes on writing good Acceptance Tests:

* Scenario title: "That time when...". i.e. `Scenario: A clinician updated a patient's registration`
* The Web World is only used by the `When` statements.  `Given` statements prepares the
scenario using direct-model access, not the UI. `Then` statements verifies the scenario using direct-model access, again, not the UI.
* View the feature [Changing the Waitlist Status](https://github.com/airslie/renalwarev2/blob/master/features/renalware/transplants/changing_the_wait_list_status.feature) of a good example
