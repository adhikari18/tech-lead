# Code Quality

## Introduction:
Using SonarQube with a .NET Core project can help ensure code quality and enforce coding standards. SonarQube analyzes your codebase, identifies code smells, vulnerabilities, bugs, and provides detailed information on how to address them, all while following established coding standards.

To set up and enforce coding standards using SonarQube with a .NET Core project, follow these steps:

### Setup SonarQube:
- You can use the SonarQube server locally, or deploy it on a server or cloud. Make sure you've installed it and have it running.
- Install the necessary plugins for C# analysis from the SonarQube marketplace.
- Install SonarScanner for .NET:

### Install the SonarScanner for .NET.
- Integration with .NET Core:
- Begin the SonarQube analysis:

```bash
dotnet sonarscanner begin /k:"YourProjectKey" /d:sonar.login="YourToken" /d:sonar.host.url="YourSonarQubeURL"
```

Replace `YourProjectKey`, `YourToken`, and `YourSonarQubeURL` with appropriate values.

Build your project:

```bash
dotnet build YourSolution.sln
```

Complete the SonarQube analysis:
```bash
dotnet sonarscanner end /d:sonar.login="YourToken"
```

### Review Analysis on SonarQube Dashboard:
After the analysis is completed, you can view the results on your SonarQube dashboard. It will show vulnerabilities, code smells, bugs, and coverage.

### Examples of Coding Standards:

SonarQube provides numerous rules for C#. Here are some examples of coding standards and best practices it checks for:

#### Code Complexity: Methods or classes that have high cyclomatic complexity.

```csharp
public int ComplexMethod(int a) {  // too many branching conditions
    if(a == 1) { /*...*/ }
    else if(a == 2) { /*...*/ }
    // ...
    else if(a == 10) { /*...*/ }
    return a;
}
```
SonarQube might flag this for refactoring.

#### Unused Variables:

```csharp
public void SomeMethod() {
    var unusedVar = "I'm not used";  // unused variable
    Console.WriteLine("Hello, world!");
}
```

#### Null Reference Checks:

```csharp
public string GetName(Person p) {
    return p.Name;  // potential null reference
}
```

#### Duplicate Code Blocks:
SonarQube can identify blocks of code that are duplicated, suggesting potential refactoring.

#### Naming Conventions: 
Ensures classes, methods, and variables follow established naming conventions.

#### Code Coverage: 
With integration to tools like Coverlet, SonarQube can also provide insights into your code coverage.

#### Enforcing the Standards:

##### Quality Gates:
In SonarQube, set up Quality Gates to define the criteria that your code must meet before being considered as 'releasable'. For instance, you might set a threshold for code coverage or the maximum number of critical issues.
##### Fail Builds: Integrate SonarQube with your CI/CD pipeline to fail builds that don't meet the criteria set in your Quality Gates.

#### Continuous Monitoring:
Regularly review the SonarQube dashboard and address issues. It's essential to treat the feedback as an integral part of the development cycle, fostering a culture of code quality within the team.

### Conclusion
By using SonarQube effectively, you can ensure that your C# .NET Core project not only works correctly but is also maintainable, efficient, and follows best practices.