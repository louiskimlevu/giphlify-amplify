## Deploy the Site

Finally, we need to add hosting to deploy our frontend.

First, we need to push this tutorial code to GitHub by:

- creating a new repository by clicking the plus button on the top right of the page.
- choose a repository name and click `create repository`
- Then, copy the commands from `…or push an existing repository from the command line` and run them in your terminal.

```
git config --global user.email "louiskim.levu@gmail.com"
git config --global user.name "Louis Kim Le Vu"
```

Run git add . && git commit -m "tutorial complete" && git push in your terminal to send your latest changes.

```
git add .
git commit -m "first commit"
git remote add origin https://github.com/louiskimlevu/giphlify.git
git branch -M main
git push -u origin main
```

Then, you can run the command: `$ amplify add hosting`. Select `Continuous deployment (Git-based deployments)` for the first question and then head to the Amplify Console when it pops up.
**AWS Amplify Console**

- Choose GitHub in the `From your existing code` menu, and click continue
- Type in the name of your GitHub repo you just created (it should autofill!) and then click next.
- If required, create `amplifyconsole-backend-role` with full AdministratorAccess
- The build settings will auto-populate, though you need to edit it:
- Download the amplify.yml file and add it to the root of your repository.
- Edit amplify.yml change the `baseDirectory` under `artifacts` to `dist`:

```yaml

---
artifacts:
  baseDirectory: dist
```

- git add . && git commit -m "add build settings" && git push -u origin main
- Run again `amplify add hosting` and run through the same steps, this time amplify.yml should be detected
- Click save and deploy
- This will deploy our frontend app to Amplify backed by S3 but bucket is not accessible
  It may take a few minutes, but then you'll have your application up and ready for anyone to visit.

For the first 12 months of your AWS account existing, Amplify and Appsync, which we're using for the api, has a free tier that will most likely cover your hosting. After that, here is more information about API hosting and here is more information about static site hosting!

## Conclusion

In this tutorial, we built a fullstack CRUD app with JavaScript, HTML, CSS, and AWS Amplify. We were able to use AWS Amplify's generated GraphQL queries and mutations to interact with our data. We also deployed the frontend to AWS Amplify Hosting. A few next steps could be to add user authentication or allow users to upload their images instead of just posting links. If you have any questions about this tutorial, please tweet me!
