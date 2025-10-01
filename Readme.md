🚀 Raya Assessment – Verify Account Position (WI1)


![image alt](perofmer.gif)
![image alt](Dispatcher.gif)
# Project Analysis

This UiPath RPA project automates the verification of account positions in ACME System 1, following the robust REFramework pattern. The solution is split into two main components for scalability and maintainability:

## Dispatcher
- **Purpose:** Extracts work items from ACME System 1 and loads them into an Orchestrator Queue.
- **Key Steps:**
    - Initializes applications and configuration.
    - Extracts data from ACME System 1.
    - Adds extracted data to the Orchestrator Queue for processing.
- **Main Workflows:**
    - `Main.xaml`: Controls the overall dispatcher flow.
    - `InitAllSettings.xaml`: Loads configuration and assets.
    - `InitAllApplications.xaml`: Initializes ACME System 1.
    - `GetTransactionData.xaml`: Retrieves and queues work items.
    - `CloseAllApplications.xaml`: Cleans up and closes applications.

## Performer
- **Purpose:** Processes queue items and executes account verification logic in ACME System 1.
- **Key Steps:**
    - Retrieves transaction items from the queue.
    - Navigates ACME System 1 to verify accounts.
    - Applies business rules, updates status, and handles exceptions.
    - Logs out and cleans up applications.
- **Main Workflows:**
    - `Main.xaml`: Controls the overall performer flow.
    - `Process.xaml`: Executes the core verification logic.
    - `SetTransactionStatus.xaml`: Updates transaction outcome.
    - `RetryCurrentTransaction.xaml`: Handles retries for failed items.
    - `ApplicationCrashedEmail.xaml`: Sends crash notifications.

# Prerequisites
- UiPath Studio and Robot installed and connected
- UiPath Orchestrator Queue configured
- Access credentials for ACME System 1
- Populated configuration file at `Data\Config.xlsx`
- Orchestrator Assets for secure credential storage

# Project Structures
---

## Assets Used

### Dispatcher
- **ACME_System_Credentials**: Secure credential asset for ACME System 1 login
- **Email_Credentials**: Credentials for sending exception notification emails
- **Config**: Configuration settings loaded from Orchestrator assets and Data/Config.xlsx

### Performer
- **ACME_System_Credentials**: Secure credential asset for ACME System 1 login
- **Email_Credentials**: Credentials for sending exception notification emails
- **Config**: Configuration settings loaded from Orchestrator assets and Data/Config.xlsx

---

## Dispatcher Structure
RAYA_UiPath_VerifyAccountPositions_Dispatcher/
├── ACMEWeb/
│   ├── ACMEWeb_ExtractWorkItems.xaml
│   ├── ACMEWeb_InitializeApp.xaml
│   ├── ACMEWeb_Login.xaml
│   └── ACMEWeb_NavigateWorkItems.xaml
├── Common/
│   ├── Control/
│   │   ├── Common_CheckAppCrash.xaml
│   │   └── Common_CloseApp.xaml
│   └── Email/
│       └── Email_SendExceptionMail.xaml
├── Data/
│   ├── Config.xlsx
│   ├── Input/
│   │   ├── EmailTemplate.html
│   │   └── placeholder.txt
│   ├── Output/
│   │   └── placeholder.txt
│   └── Temp/
│       └── placeholder.txt
├── Dispatcher/
│   └── Dispatcher_DispatchWorkItems.xaml
├── Documentation/
│   └── REFramework Documentation-EN.pdf
├── Exceptions_Screenshots/
│   ├── ExceptionScreenshot_251001.030834.png
│   ├── ExceptionScreenshot_251001.044032.png
│   ├── ExceptionScreenshot_251001.044711.png
│   ├── ExceptionScreenshot_251001.110127.png
│   ├── ExceptionScreenshot_251001.111102.png
│   ├── ExceptionScreenshot_251001.124209.png
│   ├── ExceptionScreenshot_251001.124932.png
│   └── placeholder.txt
├── Framework/
│   ├── CloseAllApplications.xaml
│   ├── ExtractAndUploadQueueItems.xaml
│   ├── InitAllApplications.xaml
│   ├── InitAllSettings.xaml
│   ├── KillAllProcesses.xaml
│   ├── RetryCurrentTransaction.xaml
│   ├── SetTransactionStatus.xaml
│   └── TakeScreenshot.xaml
├── Tests/
│   ├── InitAllApplicationsTestCase.xaml
│   ├── InitAllSettingsTestCase.xaml
│   ├── MainTestCase.xaml
│   ├── ProcessTestCase.xaml
│   ├── Tests.xlsx
│   └── WorkflowTestCaseTemplate.xaml
├── LICENSE
├── Main.xaml
├── Main.xaml.json
├── project.json
└── README.md

## Performer Structure
RAYA_UiPath_VerifyAccountPositions_Performer/
├── ACMEDesktop/
│   ├── ACMEDesktop_InitializeApp.xaml
│   ├── ACMEDesktop_Login.xaml
│   ├── ACMEDesktop_NavigateToAccountTransactions.xaml
│   ├── ACMEDesktop_NavigateToClientAccounts.xaml
│   ├── ACMEDesktop_NavigateToClientDetails.xaml
│   ├── ACMEDesktop_NavigateToClientSearch.xaml
│   ├── ACMEDesktop_SumAccountTransactions.xaml
│   └── Control/
│       └── ACMEDesktop_ControlTabs.xaml
├── ACMEWeb/
│   ├── ACMEWeb_ExtractWorkItemData.xaml
│   ├── ACMEWeb_InitializeApp.xaml
│   ├── ACMEWeb_Login.xaml
│   ├── ACMEWeb_NavigateToUpdateWorkItem.xaml
│   ├── ACMEWeb_NavigateWorkItems.xaml
│   └── ACMEWeb_UpdateWorkItem.xaml
├── Common/
│   ├── Control/
│   │   ├── Common_CheckAppCrash.xaml
│   │   ├── Common_CloseApp.xaml
│   │   └── Control_CheckAccountPosition.xaml
│   └── Email/
│       └── Email_SendExceptionMail.xaml
├── Data/
│   ├── Config.xlsx
│   ├── Input/
│   │   ├── EmailTemplate.html
│   │   └── placeholder.txt
│   ├── Output/
│   │   └── placeholder.txt
│   └── Temp/
│       └── placeholder.txt
├── Documentation/
│   └── REFramework Documentation-EN.pdf
├── Email/
│   └── Email_SendExceptionMail.xaml
├── Exceptions_Screenshots/
│   └── placeholder.txt
├── Framework/
│   ├── CloseAllApplications.xaml
│   ├── GetTransactionData.xaml
│   ├── InitAllApplications.xaml
│   ├── InitAllSettings.xaml
│   ├── KillAllProcesses.xaml
│   ├── Process.xaml
│   ├── RetryCurrentTransaction.xaml
│   ├── SetTransactionStatus.xaml
│   └── TakeScreenshot.xaml
├── Tests/
│   ├── GetTransactionDataTestCase.xaml
│   ├── InitAllApplicationsTestCase.xaml
│   ├── InitAllSettingsTestCase.xaml
│   ├── MainTestCase.xaml
│   ├── ProcessTestCase.xaml
│   ├── Tests.xlsx
│   └── WorkflowTestCaseTemplate.xaml
├── LICENSE
├── Main.xaml
├── Main.xaml.json
├── project.json
└── README.md

# Email Templates
- `AcmeSystemIsntOpenBody.html`: Triggered when ACME System 1 is not accessible
- `ApplicationCrashedEmail.html`: Triggered on application crash (AE01)
- `WrongCredaitialsEmailTemplate.html.html`: Triggered when login credentials are invalid

# Summary

# Packages

The following UiPath packages are required for this solution:
- UiPath.System.Activities
- UiPath.UIAutomation.Activities
- UiPath.Excel.Activities
- UiPath.Mail.Activities
- UiPath.WebAPI.Activities
- UiPath.Credentials.Activities
- UiPath.Testing.Activities (for test workflows)

---

This automation ensures reliable and scalable account position verification by:
- Separating Dispatcher and Performer for modularity
- Leveraging REFramework for resilience and error handling
- Using UiPath Orchestrator for transaction management and monitoring
