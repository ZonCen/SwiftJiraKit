
# SwiftJiraKit

SwiftJiraKit is a lightweight and modular Swift library for interacting with Jira's REST API (version 2). It simplifies tasks like logging work time and managing Jira issues, making it ideal for developers who want an easy-to-use solution for Jira API integration in their Swift projects.

## Features

- Log work time on Jira issues with minimal effort.
- Modular design for future extensions (e.g., fetching issues, comments, etc.).
- Built-in support for Bearer token authentication.
- Clean and extensible API interface.

## Installation

SwiftJiraKit is distributed as a Swift Package Manager (SPM) package. Add the following to your `Package.swift`:

```swift
dependencies: [
    .package(url: "https://github.com/martindahlswe/SwiftJiraKit.git", from: "1.0.0")
]
```

Then import it into your project:

```swift
import SwiftJiraKit
```

## Usage

### 1. Initialize JiraAPI

Start by creating an instance of `JiraAPI` with your Jira instance's base URL and your personal access token (PAT):

```swift
let jiraAPI = JiraAPI(baseURL: "https://your-jira-instance.atlassian.net", token: "your-personal-access-token")
```

### 2. Log Work Time

Log work time for an issue using the `WorklogService`:

```swift
jiraAPI.worklogService.logWork(
    issueKey: "PROJECT-123",
    timeSpentSeconds: 3600,  // 1 hour
    started: "2024-01-01T12:00:00.000+0000",  // ISO8601 format
    comment: "Implemented feature X"
) { result in
    switch result {
    case .success(let response):
        print("Worklog added with ID: \(response.id)")
    case .failure(let error):
        print("Failed to log work: \(error)")
    }
}
```

### 3. Fetch Issue Details (Coming Soon)

Stay tuned for updates as more features like fetching issue details and adding comments are implemented.

## Contributing

Contributions are welcome! If you have an idea or find a bug, feel free to open an issue or submit a pull request.

1. Fork the repository.
2. Create a new branch: `git checkout -b feature/your-feature`.
3. Commit your changes: `git commit -m 'Add some feature'`.
4. Push to the branch: `git push origin feature/your-feature`.
5. Open a pull request.

## License

This project is licensed under the [MIT License](LICENSE). You are free to use, modify, and distribute this software for any purpose. Attribution is appreciated but not required.

## Acknowledgements

- Thanks to the Jira REST API team for providing comprehensive documentation.
- Built with ❤️  by Martin Dahl.