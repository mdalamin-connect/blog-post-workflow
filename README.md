# Blog post workflow  [![Build and test](https://github.com/gautamkrishnar/blog-post-workflow/workflows/Build%20and%20test/badge.svg?branch=master)](https://github.com/gautamkrishnar/blog-post-workflow/actions?query=workflow%3A%22Build+and+test%22)

![preview](https://user-images.githubusercontent.com/8397274/88047382-29b8b280-cb6f-11ea-9efb-2af2b10f3e0c.png)


## How to use

1. Star this repo 😉 
1. Go to your repository
1. Add the following section to your **README.md** file, you can give whatever title you want. Just make sure that you use `<!-- BLOG-POST-LIST:START --><!-- BLOG-POST-LIST:END -->` in your readme. The workflow will replace this comment with the actual blog post list: 
    ```markdown
    # Blog posts
    <!-- BLOG-POST-LIST:START -->
    <!-- BLOG-POST-LIST:END -->
    ```
1. Create a folder named `.github` and create a `workflows` folder inside it, if it doesn't exist.
1. Create a new file named `blog-post-workflow.yml` with the following contents inside the workflows folder:
    ```yaml
    name: Latest blog post workflow
    on:
      schedule: # Run workflow automatically
        - cron: '0 * * * *' # Runs every hour, on the hour
      workflow_dispatch: # Run workflow manually (without waiting for the cron to be called), through the GitHub Actions Workflow page directly
    permissions:
      contents: write # To write the generated contents to the readme
    
    jobs:
      update-readme-with-blog:
        name: Update this repo's README with latest blog posts
        runs-on: ubuntu-latest
        steps:
          - name: Checkout
            uses: actions/checkout@v3
          - name: Pull in dev.to posts
            uses: gautamkrishnar/blog-post-workflow@v1
            with:
              feed_list: "https://dev.to/feed/gautamkrishnar,https://www.gautamkrishnar.com/feed/"
    ```
1. Replace the above URL list with your own RSS feed URLs. See [popular-sources](#popular-sources) for a list of common RSS feed urls.
1. Commit and wait for it to run automatically, or you can also trigger it manually to see the result instantly. To trigger the workflow manually, please follow the steps in the [video](https://www.youtube.com/watch?v=ECuqb5Tv9qI&t=272s).

                                                                                                                                                                                                                                                                                                                          | No       |


## Liked it?

Hope you liked this project, don't forget to give it a star ⭐.

<a href="https://starchart.cc/gautamkrishnar/blog-post-workflow">
    <img alt="chart" src="https://starchart.cc/gautamkrishnar/blog-post-workflow.svg" width="600px">
</a>
