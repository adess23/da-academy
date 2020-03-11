# Fundamentals: Python and Linux

<p align="center"> 
<img src="../assets/fundamentals.png"> 
</p>

### Motivation ###

DA needs to be ready to code. Python is the best programming language to start. We need to be sure that the trainees are decent programmers and have the desired minimum skills.

### What you will learn ###

Software development with Python

### Courses: ###

#### Python

**Mandatory:**

Choose one of these:

1. [Python for beginners](https://www.youtube.com/playlist?list=PLlrxD0HtieHhS8VzuMCfQD4uJ9yne1mE6)

2. [Acamica Python Training](https://globant.acamica.com/cursos/485/)

**Recommended:**

3. [Python Advanced](https://globant.acamica.com/cursos/488/)

**Extra:**

4. [Programming with Python: Hands-On Introduction for Beginners](https://www.udemy.com/python-programming-beginners/) (3.5h)

5. [Introduction To Python Programming](https://www.udemy.com/pythonforbeginnersintro/) (4.5h)

6. [Python Core and Advanced](https://www.udemy.com/python-core-and-advanced/) (8h)

7. [Python from Beginner to Intermediate in 30 min.](https://www.udemy.com/python-from-beginner-to-expert-starter-free/) (1.5h)

8. [Learn Python 3.6 for Total Beginners](https://www.udemy.com/python-3-for-total-beginners/) (6.5h)

9. [Python Basics - Bootcamp](https://www.udemy.com/python-basics-bootcamp/) (45m)

10. [Learn Python 3 From Scratch | Python for Absolute Beginners](https://www.udemy.com/learn-python-3-from-scratch-python-for-absolute-beginners/) (2.5h)

11. [Python 101: Unlock Programm Skills - From Novice to Expert](https://www.udemy.com/python-101-unlock-programming-skills/) (4.5h)


#### Linux

**Mandatory:**
1. [Introduction to Linux](https://www.edx.org/course/introduction-to-linux)
- Mandatory Chapters: 3, 7, 8, 9, 10, 11, 12, 14, 16, 18
- All other chapters are recommended but not obligatory

**Extra:**
2. [Linux Fundamentals for IT Professionals](https://www.udemy.com/linux-fundamentals-for-it-professionals/) (8h)

3. [Intro to Linux Shell Scripting](https://www.udemy.com/linux-shell-scripting-free/) (42m)


→ [index](#index)

### Practice: ###

#### Before you begin ####
(It is assumed that Git is already installed and working).

1. **Fork** this repository.
2. Clone your fork.
3. Initialize a simple project in your local repository.
4. Update *.gitignore* file, not to upload */target* folder nor any undesirable and unneeded file.
5. Upload your code with whatever changes you've made. You will upload your individual progress in your master branch. You can also create additional branches for testing/other purposes. Corrections will be only made against your master branch.
6. Every practice functionality must be validated through unit tests. Use the [pytest package](https://pytest.readthedocs.io/en/latest/getting-started.html) to make these tests.

#### Exercices ####

1. **Linux basics**: Answer the following questions:

- What command would you use to count the amount of occurrences of the word ​Unix ​in a file? How would make the command case insensitive?
- What command would you use to constantly see the last 100 lines appended to a file that contain the word ​*"ERROR"*​?

2. **Python Basics**: Matrix Calculation

Create a class which allows to represent a matrix of any order or shape (n x n, n x m). It should also allow the following operations with matrices:

- Matrices addition
- Scalar multiplication
- Matrices multiplication
- Matrix transpose
- Matrix determinant
- Adjugate matrix
- Inverted matrix

Add additional methods:

- A method to obtain a matrix row. Do not return repeated rows. E.g., you can specify that the rows 1,3,8 are desired from a 20x10 matrix.

- A method to obtain a matrix column. Do not return repeated columns. E.g., you can specify that the columns 2,4,10 are desired from a 20x10 matrix.

- A method to obtain part of the matrix from a certain column. E.g., from a 10x10 matrix, the 10x2 matrix from column 5 is desired.

- A method to show the matrix on screen as a matrix.

A 3x6 matrix can be defined at the class instantiation time like this:
Matrix([[1,2,3,4,5,6],
	[10,11,12,13,14,15],
	[-1,-2,-3,-4,-5,-6]])

Do not use the numpy package for this implementation. Just use the Standard Library.

[Matrix calculation reference](
http://matematicasbachiller.com/videos/2-bachillerato/introduccion-al-algebra-de-lo-lineal/01-calculo-matricial-6)

#### Deploying to the Cloud ####

After having finished with your exercices, upload them to your Cloud Storage bucket within a folder called *Week_0*. 

### Commit: ###

Commit your practice code.

<img src="../assets/stop.png" title="Stop Logo" width="150" height="150">

### Auto assessment: ###

*1. Linux: What is the difference between a partition and a filesystem?*

*2. What is the relationship between Linux Kernel and Linux Distros?*

*3. What are the two levels on which the package managers operate on Linux?*

*4. How would you go about researching a new feature on Linux? How are the different sources of documentation used?*

*5. What are the different types of processes? How do you manage them?*

*6. Explain the concepts of partitions, mount points, NFS and pseudo filesystems*

*7. How does a Network work? What are the different types of addresses? What is the function of the DNS? What happens when you send a file using FTP?*

*8. How do you use routines on bash scripts? Why would you use bash scripting?*

*9. What steps should you take to make Linux as secure as possible? What is process isolation, and how do you achieve it? How can you secure the boot process?*

*10. What does it that Python is: Interpreted, Dynamic typing, Extensive, Object Oriented*

*11. Python Data Structures and characteristics? Differences and similarities between dictionary, map, set, lists and tuples*

*12. What are Lambda Expressions? What are Nested statements? How can you create and use each of them? Why would you?*

*13. Explain the concept of Inheritance. How does it work?*

*14. Explain the concept of Polymorphism. How does it work?*

*15. What are errors and exceptions in python? How can you handle them?*

*16. Explain all the built-in functions you can remember*

*17. What are decorators in python? Why would you use them, and how?*

*18. What is the difference between generators and iterators? How can you create and consume a generator?*

*19. What are python coding conventions? How would you go about creating a python project from scratch? How would you structure it?*

*20. What are the different ways of debugging your python project? Why and how would you use each of them?*

---

<img src="../assets/get_badge.png"> 

### *Sync to obtain your badge!*
 
Remember to sync with an Academy tutor to obtain your badge before continuing to the next module. This will also let you be sure you have acquired every needed concept. Complete the [Ending Module form](https://forms.gle/ukvWjKtoFYx4Kn8q7) and a tutor will ping you to schedule the evaluation date. If not being noticed after 7 days, feel free to remind any of the tutors about it.
