How to create a Java library (JAR file) that is accessible over the internet (public lib) using maven as a build tool

I’ll walk you through the process of creating a simple Java library (JAR file) and making it public or private so that anyone (internet or a team) can use it in their own projects.

Use Case: This is useful for sharing reusable code with the community (For open source Contributions) or for internal use across different projects.
This allows open source developers to collaborate with each other and allows internal teams to share the same functionality across various projects or microservices.



For example, if you’ve written a linear regression algorithm in Java and want to use it across multiple projects, you can package it into a Java library (JAR file).
Instead of copying the code each time, you only need to maintain it in one place. By importing the library as a Maven dependency in new projects, you save time and ensure consistency, making it easy for you and others to reuse and share the functionality.



Step 1: Create the Java Library Project

Start by creating a new Java project using Maven. You can do this easily in an IDE like IntelliJ IDEA or eclipse. 

Maven uses a standardized directory structure to organize Java projects. In this structure, the src/main/java folder is where you write the code for your library. For example, if you’re building a math helper library, you would create Java files inside this src folder (and then your package) to define methods for operations like addition, subtraction, and multiplication. This structure helps Maven easily locate and build your code while keeping everything organized, making it simple for others to use your library in their own projects.

Step 2: Set up Maven and create a pom.xml file

Maven uses a special file called pom.xml (Project Object Model) to manage your project’s dependencies and build configuration. In this step, you need to create this file at the root of your project. The pom.xml file tells Maven how to build your project, what dependencies your library needs, and other important details. For example, you’ll specify the group ID, artifact ID, and version for your library, which are like identifiers for your library. You also define any dependencies your library needs (like external libraries) and any plugins to help with building and packaging the library.

Here is an example of a simple pom.xml file for your library:

https://github.com/Fakipo/mathhelper/blob/main/pom.xml

This file is crucial for Maven to understand how to handle your project and make it easily accessible to others. Make sure to update the groupId, artifactId, and version to match your own project details.


Step 3: Writing the Code

Once your project is set up, it’s time to write the code for your library. The key is to keep your code modular, meaning that each function should perform a single, specific task. For instance, in a math helper library, you could write simple functions like add(), subtract(), and multiply() to handle individual operations. It's important to keep these functions simple and focused, avoiding combining multiple tasks in one method.

You can check out the below example for reference

https://github.com/Fakipo/mathhelper/blob/main/src/main/java/helper/MathHelper.java

Step 4: Build the JAR

After writing the code, the next step is to build the JAR file. In Maven, this can be done with the mvn clean package command. This command compiles your code, runs tests, and packages your project into a JAR file located in the target/ folder. This JAR file is what will be shared and used as the library in other projects.


Step 5: Configure your Github repo

Once your code is ready, you need to upload the JAR to GitHub Packages to make it available as a Maven dependency. First, create a GitHub repository and push your code there. Then, configure your pom.xml to include GitHub Packages as the repository for your library (as shown in the earlier example of pom.xml). 


Step 6: Update Settings.xml and maven deploy

To upload your JAR file to GitHub Packages, you need to set up authentication first. This is done by adding your GitHub token to a file called settings.xml in the .m2 folder. On macOS or Linux, the .m2 folder is usually located in your home directory (~/.m2/), while on Windows, it can be found in C:\Users\YourUsername\.m2. If the folder or file doesn’t exist, you can create them. Add your GitHub token to the settings.xml file, which allows Maven to authenticate with GitHub. After that, use the mvn deploy command in your terminal or IntelliJ (using maven UI) to upload the JAR file to GitHub Packages. Once uploaded, others can easily add it as a dependency in their Maven projects and start using it.

After successfully uploading your JAR file to GitHub Packages, navigate to your GitHub repository and go to the "Packages" section. There, you’ll find your library listed with the version number. GitHub will provide you with a Maven dependency snippet that you can copy and paste into the <dependencies> section of your own pom.xml file. This will allow you to easily import your library into any project and start using the methods and functionalities you’ve written.


Below is an example of my created JAR file for a small Math helper package

https://github.com/Fakipo/mathhelper/packages/2430298

