name: 🐞 Bug Report
description: 버그가 발생했을 때 사용
title: "[BUG] "
labels: ["bug"]
assignees: []

body:
  - type: markdown
    attributes:
      value: |
        ## 🐞 버그 설명
  - type: input
    id: bug-description
    attributes:
      label: 버그 설명
      placeholder: 어떤 문제가 발생했는지 작성해주세요
    validations:
      required: true

  - type: textarea
    id: steps
    attributes:
      label: 재현 방법
      placeholder: 어떤 순서로 버그를 재현했는지 작성해주세요
    validations:
      required: false

  - type: textarea
    id: expected
    attributes:
      label: 기대한 동작
      placeholder: 원래 어떻게 동작했어야 하는지
    validations:
      required: false

