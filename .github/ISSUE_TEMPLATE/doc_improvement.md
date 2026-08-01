name: Documentation Improvement
description: Suggest an improvement or fix for repository documentation
title: "[DOC]: "
labels: ["documentation"]
assignees: []
body:
  - type: textarea
    id: description
    attributes:
      label: Description of Issue / Improvement
      description: Provide a clear description of the documentation fix or broken link.
    validations:
      required: true
  - type: textarea
    id: proposed_fix
    attributes:
      label: Proposed Solution
      description: Describe the fix or updated text you suggest.
    validations:
      required: false
