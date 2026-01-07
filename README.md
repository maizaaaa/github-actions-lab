[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/x7qwpQ24)
## Tutorial-17: GitHub Action

## Student Info:
1. Matric Number: 302755
2. Name: Nurul Maizatul Hasanah Binti Noor Azlan


## 🎯 Objective
By the end of this tutorial, students should be able to:
1. Explain the difference between workflow, job, and step
2. Create a simple GitHub Actions workflow
3. Observe how jobs run in parallel, and steps run sequentially
4. Modify the workflow to add a job dependency


## Instructions

### Part A: Repository Setup
1. Create a new GitHub repository
- Name: github-actions-lab
- Public repository
- Add a README file

2. Inside the repository, create this folder:
```
.github/workflows/
```
3. Create a file named:
```
lab-actions.yml
```

### Part B: Create Your First Workflow
Paste the following code into `lab-actions.yml`:
```yml
name: Workflow vs Job vs Step Lab

on: push

jobs:
  job-one:
    runs-on: ubuntu-latest
    steps:
      - name: Step 1 - Print message
        run: echo "This is Step 1 in Job One"

      - name: Step 2 - Print another message
        run: echo "This is Step 2 in Job One"

  job-two:
    runs-on: ubuntu-latest
    steps:
      - name: Step 1 - Print message
        run: echo "This is Step 1 in Job Two"
```
>Commit and push the file.

### Part C: Observe the Execution
1. Go to Actions tab in GitHub
2. Click the running workflow
3. Observe:
   - The workflow name
   - Two jobs running in parallel
   - Steps executing top to bottom inside each job

### Part D: Add Job Dependency
Now modify job-two so it runs after job-one. Update the file:
```yml
job-two:
  needs: job-one
  runs-on: ubuntu-latest
  steps:
    - name: Step 1 - Print message
      run: echo "Job Two runs after Job One"
```
>Commit and push again.

### Part E: Compare Results
You should now observe:
- job-one runs first
- job-two waits until job-one finishes


## Submission
Screenshot of:
1. Workflow page
2. Job execution view

## Results
Result Workflow page:
<img width="959" height="536" alt="image" src="https://github.com/user-attachments/assets/c7719b98-7b2b-439c-8efd-c6480042ab8a" />

Result job-one runs first:
<img width="1916" height="1064" alt="Screenshot 2026-01-07 214345" src="https://github.com/user-attachments/assets/0b308ef3-dfbf-4b62-b3d9-14ca0a742555" />

Result job-two waits until job-one finishes:
<img width="959" height="536" alt="image" src="https://github.com/user-attachments/assets/3827c0f5-4154-463b-8367-b845259f9b9c" />







