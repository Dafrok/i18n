# Electron 이슈

* [이슈에 기여하는 방법](#how-to-contribute-to-issues)
* [일반적인 도움받기](#asking-for-general-help)
* [버그 신고하기](#submitting-a-bug-report)
* [버그 보고서 작성](#triaging-a-bug-report)
* [버그 리포트 해결](#resolving-a-bug-report)

## 이슈에 기여하는 방법

어떤 이슈든, 개인이 근본적으로 기여할수 있는 3가지 방법이 있습니다.:

1. By opening the issue for discussion: If you believe that you have found a new bug in Electron, you should report it by creating a new issue in the [`electron/electron` issue tracker](https://github.com/electron/electron/issues).
2. By helping to triage the issue: You can do this either by providing assistive details (a reproducible test case that demonstrates a bug) or by providing suggestions to address the issue.
3. By helping to resolve the issue: This can be done by demonstrating that the issue is not a bug or is fixed; but more often, by opening a pull request that changes the source in `electron/electron` in a concrete and reviewable manner.

## 일반적인 도움받기

["Finding Support"](../tutorial/support.md#finding-support) has a list of resources for getting programming help, reporting security issues, contributing, and more. Please use the issue tracker for bugs only!

## 버그 신고하기

To submit a bug report:

When opening a new issue in the [`electron/electron` issue tracker](https://github.com/electron/electron/issues/new/choose), users will be presented with [a template](https://github.com/electron/electron/blob/master/.github/ISSUE_TEMPLATE/Bug_report.md) that should be filled in.

If you believe that you have found a bug in Electron, please fill out the template to the best of your ability.

The two most important pieces of information needed to evaluate the report are a description of the bug and a simple test case to recreate it. It is easier to fix a bug if it can be reproduced.

See [How to create a Minimal, Complete, and Verifiable example](https://stackoverflow.com/help/mcve).

## 버그 보고서 작성

It's common for open issues to involve discussion. Some contributors may have differing opinions, including whether the behavior is a bug or feature. This discussion is part of the process and should be kept focused, helpful, and professional.

Terse responses that provide neither additional context nor supporting detail are not helpful or professional. To many, such responses are annoying and unfriendly.

Contributors are encouraged to solve issues collaboratively and help one another make progress. 잘못되었다고 생각하거나 잘못된 정보가 포함된 문제가 발생한다면 추가 지원 컨텍스트를 통해 왜 그런 느낌이 들었는지 설명하고 자신이 틀렸다고 확신할 수 있습니다. By doing so, we can often reach the correct outcome faster.

## 버그 리포트 해결

주요 이슈들은 Pull Request를 열어 해결합니다. The process for opening and reviewing a pull request is similar to that of opening and triaging issues, but carries with it a necessary review and approval workflow that ensures that the proposed changes meet the minimal quality and functional guidelines of the Electron project.
