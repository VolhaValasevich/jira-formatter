# jira-formatter

## Usage

Add the reporter configuration to your Cucumber config file.

```
module.exports = {
  default: {
    format: [
      './src/formatter.js',
    ],
    formatOptions: {
      jiraOptions: {
        endpoint: 'http://localhost:8080',
        token: '123456789',
        execution: 'PC-7',
        resetTests: ['PC-1', 'PC-2', 'PC-3'],
        regexp: /(PC-\d+)/,
        report: path.resolve('./test/xray.json')
      }
    }
  }
}
```

### Options

| Name         | Type         | Example                          | Description                                                                                                           | Optional |
|--------------|--------------|----------------------------------|-----------------------------------------------------------------------------------------------------------------------|----------|
| `regexp`     | `RegExp`     | `/@jira\((\w+-\d+)\)/`           | Regular expression for getting a test's Jira ID from its tags. The first capturing group should return the ID.        | No       |
| `report`     | `string`     | `./report/xray.json`             | Path to the file where the xray report will be saved.                                                                 | Yes      |
| `endpoint`   | `string`     | `https://jira.company.com/jira/` | Your Jira endpoint.                                                                                                   | Yes      |
| `token`      | `string`     |                                  | Jira API token. See [docs](https://confluence.atlassian.com/enterprise/using-personal-access-tokens-1026032365.html). | Yes      |
| `execution`  | `string`     | `PC-7`                           | The ID of your Xray Test Execution.                                                                                   | Yes      |    
| `resetTests` | `string[]`   | `['PC-1', 'PC-2', 'PC-3']`       | An array of tests which should be reset in 'TODO' status before the run.                                              | Yes      |
| `pageLimit`  | `number`     | `100`                            | Max number of items returned by Xray API. Default is 200, set to another number if you have custom settings.          | Yes      |

