Validation Topics
-----------------

-   List of current rules: [[ValidationRules]]
-   Currently, libSBGN rules are written in Schematron. See [[SchematronHowto]]

Syntax for @see Entries
-----------------------

Validation rules in libSBGN should be tagged with a "see" attribute that refers to an SBGN specification that points to a validation rule.

`sbgn-(SBGN_LANG_ABBREV)-L(LEVEL_NUM)V(VERSION_NUM)-(SPEC_ENTRY)#(BULLET_NUM)`

-   SBGN_LANG_ABBREV - pd, er, af
-   LEVEL_NUM - Digit
-   VERSION_NUM - Digit or number with decimal
-   SPEC_ENTRY - Digits separated by periods indicating the section where the rule is described.
-   BULLET_NUM - Digit indicating the bulleted item describing a rule.

Example: sbgn-pd-L1V1.3-3.5.2.2\#1

Rule Categories (Roles)
-----------------------

Rules are tagged using the following categories to denote severity and status.

-   error - Failure to pass this rule type results in invalidation
-   warning - Point to recommendations; failure to meet these recommendations does not result in invalidation.
-   unimplemented - Represent "stubs" for rules that remain to be implemented.
-   untestable - Rules that are that are untestable. Such rules may result from the need to have expert knowledge of a biological system to carry out the validation.
    -   Example: If more than one set of stoichiometries can be applied to the flux arcs of the process then the stoichiometry of the flux arcs must be displayed. (sbgn-pd-L1V1.3-3.5.2.1\#8)

Error Test Files
----------------

**Creators of error test files should create both the correct and incorrect cases.**

### Naming Convention

Test files containing errors are named using the following components:

ruleId-assertionId_pass/fail-errorCount_testCount (

-   Error code for rule
-   If multiple assertions are made then which one is being tested (in the order they appear in the ruleset).
-   pass/fail, whether the file passes or fail the rule followed by an error count of any existing errors.
-   Use testCount if multiple files test the same rule.
-   If multiple rules are broken, the name should take the ruleId of the first rule broken.

Example: pd10102-3_fail-1_1.sbgn

The file failed rule pd10102 assertion 3 with 1 error. If more than one file tested this rule, then the final 1 would uniquely identify this file.