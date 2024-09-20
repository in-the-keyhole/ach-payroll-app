# Keyhole ach-payroll-app
The ach-payroll-app open-source application that provides a basic example on how to process an ACH File from the NACHA network. This scenario is specific to processing an ACH File providing payroll payments where the company and employee have accounts at the same financial institution.

This payroll application does not have all the needed data validations and business rules in place to be ready for production.

The application uses basic Spring features to watch for an ACH File in a local directory, a schedule a job for applying funds, and transactional support.

## Prerequisites
Make sure you have the following installed on your machine before proceeding:

- Docker Desktop (version 4.11.0 or higher) for running MongoDB
- STS/Eclipse with Lombok for viewing the code
- Maven but this example will use the Maven wrapper

## Starting the application with Maven Wrapper
1. Clone the repository:
    ```bash
    git clone https://github.com/in-the-keyhole/ach-payroll-app.git
    cd ach-payroll-app
    ```
1. Ensure Docker Desktop is running
1. Set up Environment:  Create the directory for the file watching property application.fileWatcher.directory
1. Start MongoDB
    ```bash
     cd .\docker-compose\mongodb\ 
     docker compose up
    ```
1. Start the application
    ```bash
    .\mvnw spring-boot:run
    ```

The application should now be running and waiting for a file to be dropped in the application.fileWatcher.directory location.  There are example files at "\ach-payroll-app\src\test\resources\ach_files".  When using a file, update the Payment Effective date in the file located on the second line starting at character 70 to today's date.

After the ACH File is processed, you'll see the respective the MongoDB collection "accounts" updated with new "amount" values.  The processed payments and the final states will be reflected in the "payrollPayments" collection.

## Contributing
Created and maintained by Keyhole Software on [github](https://github.com/in-the-keyhole).

## License
Refer to the [LICENSE](./LICENSE) document.
