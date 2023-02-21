# Github Actions

Github Actions有一些自己的术语

(1) workflow（工作流程）：持续集成一次运行的过程

(2) job（任务）：一个workflow由一个或多个jobs构成，含义是一次持续集成的运行，可以完成多个任务

(3) step（步骤）：每个job由多个step构成，一步步完成

(4) action（动作）：每个step可以依次执行一个或多个命令（action）

Github Actions的配置文件叫做workflow文件，存放在代码仓库的`.github/workflows`目录

workflow文件采用YAML格式，文件名可以任意取，但是后缀名统一为`.yml`，一个仓库可以有多个workflow文件。

workflow文件的配置字段非常多，详见[官方文档](https://docs.github.com/zh/actions/using-workflows/workflow-syntax-for-github-actions)

一个完整的workflow文件的范例

```yaml
name: Greeting from Mona
on: push

jobs:
  my-job:
    name: My Job
    runs-on: ubuntu-latest
    steps:
    - name: Print a greeting
      env:
        MY_VAR: Hi there! My name is
        FIRST_NAME: Mona
        MIDDLE_NAME: The
        LAST_NAME: Octocat
      run: |
        echo $MY_VAR $FIRST_NAME $MIDDLE_NAME $LAST_NAME.
```

