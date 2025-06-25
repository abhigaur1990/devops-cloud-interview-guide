## Question  
What are Jenkins Shared Libraries and how do they work?

### 📝 Short Explanation  
Jenkins Shared Libraries allow you to **centralize reusable pipeline code** (like functions, steps, and variables) across multiple pipelines. They promote **code reuse**, **maintainability**, and **consistency** in large Jenkins setups.

## ✅ Answer  

---

### 📘 What is a Jenkins Shared Library?
As a devo’s engineer, I worked with multiple development team to create ci/cd pipeline.
which are common across multiple teams,
for ex: - stage like static code analysis which are common across development, stage liek build are common and code we write are almost also code.
So what we use across team is we use Jenkins shared libraries because Jenkins is our ci/cd tools.
SO, we created our gilt repo and within git hub repo we started creating Jenkins shared libraries and whenever we create new ci/cd pipeline we check if any exiting ci/cd pipeling can be used instead of writing ci/cd pipeline from zero.
We just involve Jenkins shared libraries within ci/cd pipeline.
SO, within Jenkins files, instead of writing code from scratch we check if that piece of code can be taken from Jenkins shared libraries if yes we invoke it.
And by this way we significantly reduce the time while creating new ci/cd pipeline and we use git hub for storing Jenkins libraries.

A **Shared Library** is a Git repository (or part of one) that contains reusable Groovy code you can include in Jenkins pipelines using the `@Library` annotation.

It typically includes:
```
(root)
├── vars/
│   └── sayHello.groovy
├── src/
│   └── org/example/MyClass.groovy
├── resources/
│   └── templates/config.xml
└── README.md
```

---

### 🧠 Why Use Shared Libraries?

- Avoid repeating logic in every Jenkinsfile  
- Encapsulate business logic, deployment steps, or validation code  
- Easy updates across all pipelines  
- Fewer errors and better collaboration  

---

### ⚙️ How Do They Work?

1. **Create a Git repo** with a specific structure (`vars/`, `src/`, etc.).
2. Configure the library in Jenkins:
   - Go to **Manage Jenkins → Global Pipeline Libraries**.
   - Add your library by name and Git URL.
3. In your Jenkinsfile, you load the library:
   ```groovy
   @Library('my-shared-library') _
   ```
4. Use global functions or classes defined in `vars/` or `src/`.

---

### 🔍 Example

**vars/sayHello.groovy**
```groovy
def call(String name = 'world') {
    echo "Hello, ${name}!"
}
```

**Jenkinsfile**
```groovy
@Library('my-shared-library') _

pipeline {
    agent any
    stages {
        stage('Greet') {
            steps {
                sayHello('Abhishek')
            }
        }
    }
}
```

---

### ✅ Benefits

- DRY (Don’t Repeat Yourself)
- Cleaner Jenkinsfiles
- Version-controlled and auditable
- Easier team collaboration

---

> Summary:  
> Jenkins Shared Libraries allow you to **modularize and reuse pipeline logic** across projects. They are ideal for **large-scale CI/CD environments** where consistency and maintainability are key.

---
