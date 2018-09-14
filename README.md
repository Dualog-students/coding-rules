### **Coding conventions**

Coding conventions create a consistent look to the code, so that readers can focus on content, not layout. They enable readers to understand the code quicker by making assumptions based on previous experience. They also facilitate copying, changing, and maintaining the code.

To achieve this we are using an EditorConfig inside each project. [EditorConfig](https://editorconfig.org) helps developers define and maintain consistent coding styles between different editors and IDEs. The EditorConfig project consists of a file format for defining coding styles and a collection of text editor plugins that enable editors to read the file format and adhere to defined styles. EditorConfig files are readable and they work nicely with version control systems.

[See this link for .NET coding convention settings examples for editorconfigs.](https://docs.microsoft.com/en-us/visualstudio/ide/editorconfig-code-style-settings-reference)

### Commit naming

All Git Commit Messages should meet the following text format:

```bash
Subject line
(One newline)
Message Body
(One newline)
Ref <###>
```

#### **Rules**

1. Capitalize the Subject.
2. Do not end the Subject line with a period.
3. Message Body should end with at least one issue tracking reference.
4. Use valid MarkDown in the message body.
5. Use the present tense ("Add feature" not "Added feature").
6. Use the **imperative** mood ("Move cursor to..." not "Moves cursor to...").
7. Use the message body to explain what and why vs. how.

*Refer to an issue describing the bug when fixing bugs.*

### **Branch naming**

*Remember: Since we are using [Waffle.io](https://waffle.io) you should always append "#issueNumber" to the branch name, this automatically moves your issue in the kanban board.*

| Naming                            | When to use?                   |
| ----------------------------------| ------------------------------ |
| `feature/awesome-branch-name`     | When developing a new feature  |
| `bugfix/awesome-branch-name`      | When fixing a bug              |
| `hotfix/awesome-branch-name`      | When fixing an urgent bug      |
| `docs/awesome-branch-name`        | When updating documentation    |
| `tooling/awesome-branch-name`     | When changing tooling          |
| `performance/awesome-branch-name` | When improving performance     |
| `refactoring/awesome-branch-name` | When refactoring code          |
| `cosmetic/awesome-branch-name`    | When improving UI/Cosmetic     |
| `testing/awesomest-branch-name`   | When adding tests              |

### **Development (GitHub) workflow**

See [GitHub workflow](https://guides.github.com/introduction/flow/) for further explanation.

#### **Starting**

When creating a new feature, you should branch off from `development` and create your own branch.
E.g.

```bash
git checkout development
git pull
git checkout -b feature/awesome-new-feature
```

#### **While working**

Try to commit your changes as you go, but commit with logical steps. This will make it easier when team-members are reviewing your code.

```shell
git add relevant-code
git commit -m "Nice commit message that follows commit-message rules"
```

If others have pushed changes to the `development` branch you can apply those changes to your branch by rebasing the branch into yours and solve any eventual conflicts locally. (`git checkout feature/awesome-new-feature && git rebase development`)

#### **When pushing changes**

If you have commits and you are not pleased with their commit messages, now is a good time to stop and fix them. Rebase your own branch by `git rebase -i HEAD^n` going `n` commits back and you'll be able to edit, squash or fixup your commits before pushing. If the last commit message is unsatisfactory you can use `git commit --amend`.

Push your changes to GitHub by

```bash
git push -u origin feature/awesome-new-feature
```

or do `git push` if you're already tracking a remote branch.

You can now create a pull request on GitHub from your branch into `development`.

Once the branch has been merged into `development` you can delete your local branch by `git branch -D feature/awesome-new-feature`. Make sure to delete the remote branch after it has been merged. This is done through the browser on GitHub or by using

```bash
git push -u -d origin feature/awesome-new-feature
```
