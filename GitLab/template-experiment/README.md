# Deployment Instructions for oTree Experiments using oForest

<!-- > ![WARNING] This page is currently under construction
> You will find the detailed docs here [devops.jasperanders.xyz](https://devops.jasperanders.xyz). -->

> Please Follow the Steps below!


## Set Up a New Experiment 

1. Fork this repository as a new project in the oForest group or subgroup. This will only work if you have at least `developer` right. The name you will give it will determine, the URL under which it will be deployed. **Watch out: You currently cannot rename your project**. It does not matter if your project is public or private.

   ![Forking on GitLab](https://www.w3schools.com/git/img_gitlab_fork.png)   

If you are planning on deploying more than a few (> 5) it can make sense to create a subgroup inside oForest first and then add your experiment to this subgroup afterward. This keeps everything tidy.

1. Now you can set the password that will be used for the admin interface of oTree. To do this, create a CI/CD variable. You will find the settings on the left hand side of your screen. Navigate to the last item in the list, called Settings and from there to `Settings > CI/CD > Variables`. Here click on the "Add Variable" button and enter:
   > - Key: `MASTER_PWD` 
   > - Value: *choose a good password. This is the password you will use to access your experiment. The password should be at least 8 characters long.*
   > - Leave the type as `Variable` and the scope as `All (default)`
   > - Check the "Flag" boxes to make it **masked** and **not protected**.
Here you can also set the oTree environment variables. They are equivalent to variables found in the otree docs. 

2. Make sure you have [GIT](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) installed.
3. Set up an **ssh key** for GitLab. For this you can consult the following [guide](https://docs.gitlab.com/ee/user/ssh.html).
4. Clone your new Project.
   ```bash
   git clone [YOUR_PROJECT_URL_HERE]
   ```
5. Open the folder on your local machine, **delete the example experiment (all the files in `src`)** and paste your oTree experiment into the `src` folder. 
6. Make sure to include **all dependencies in your `requirements.txt`**. Whenever you imported an external library (e.g. pandas, numpy, etc.) in your code, you should also add it to your requirements. If you have missing dependencies, your project won't run and the acceptance stage of the pipeline will fail.
7. If you know you need a specific python version, you can adjust it in the `Dockerfile`. Replace the `FROM python:3.9` with your version. Changing the `Dockerfile` can break your experiment, if you don't know what you are doing.
8. Finally you can commit and push your changes. If you're not sure how, please consult this [guide](https://www.atlassian.com/git).

9.  A push will trigger an automatic pipeline. This will deploy your application to `https://[Your-Project-Name].kd2experiment.iism.kit.edu`. Give it a second, as soon as you see three green checks, it is deployed. 

10. If your pipeline is failing, you can click on the red x of the respective job to get more information why this happened. If the pipeline succeeds but you still experience problems when accessing you experiment, you can run the `Get Logs` and `Describe` Jobs. If you still don't know what's wrong, contact your administrator.

11. If you want to delete your experiment or reset the database, click on `CI / CD` on the right. Here, you can trigger the `DELETE` and `RESET` jobs. 

## Updating your experiment

When you update your experiment and want to redeploy it, you can just follow the above guide starting from step *8*. You won't need to set the environment variables again. Also, note that you can make use of the management jobs to get help in troubleshooting your app.

**Watch out:** If you changed your app substantially by adding experiments or database fields, you might need to reset your database. For this, simply run the management job.

## Troubleshooting 

**Q:** I encountered an error, how can I get logs.  
**A:** The easiest way is to just visit your experiment domain.

**Q:** When I visit my experiment domain, I encounter a security warning, why?  
**A:** We use automatically issue certificates for each experiment. This can sometimes take a few moments, come back later, it should work then.


## What to do if you encounter a problem?

- Make sure you followed every step above carefully. 
- Make sure the problem is not with your code. Does it run locally on your machine?
- Only then open an Issue at the oForest project.


