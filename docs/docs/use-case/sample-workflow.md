# Sample Use Case — Workflow Test

This file is a small sample use-case diagram added separately to test the repository's diagram rendering workflow.

```plantuml
@startuml
left to right direction

actor Tester
actor "CI Workflow" as CI

rectangle "Repository Workflow" {
  usecase UC01 as "Push Code"
  usecase UC02 as "Trigger CI"
  usecase UC03 as "Run Tests"
  usecase UC04 as "Build Artifacts"
  usecase UC05 as "Deploy Test Environment"
}

Tester -- UC01
UC01 ..> UC02 : <<include>>
UC02 --> UC03
UC03 --> UC04
UC04 --> UC05

@enduml
```

<!-- diagram id="use-case-sample-workflow-file" -->

Notes: small, self-contained use-case diagram for CI/render check.
