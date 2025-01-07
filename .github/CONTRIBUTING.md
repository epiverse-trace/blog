This website is using [quarto](https://quarto.org/)
and the HTML output is automatically generated on pushes to `main`
via the [`quarto-publish.yml` GitHub Actions workflow](https://github.com/epiverse-trace/epiverse-trace.github.io/blob/main/.github/workflows/quarto-publish.yml).

All contributions should add an ORCiD for each author.

## Quarto syntax

### Linting

The validity and best usage of quarto syntax is enforced by the use of a [markdown linter as part of our continuous integration](https://github.com/epiverse-trace/.github/blob/main/workflows/lint-changed-quarto.yaml).
You can reproduce the continuous integration checks locally by running in your terminal:

```sh
npm install markdownlint-cli
npx markdownlint-cli . --dot --disable line_length first-line-h1 link-image-reference-definitions
```

### Pure quarto/markdown syntax

Whenever possible, you should prefer direct markdown/quarto syntax rather than HTML or R code.
Indeed, using HTML constrains us into outputting to a specific format,
while the strength or markdown is to be able to output in many formats.
Using R code adds a dependency to R (and possible some R packages such as knitr) which is not necessary.
Below are some examples of good vs bad practices:

- Insert a link (this specific example is checked by our linter):
  - BAD

    ```html
    <a href="https://www.example.com/">my link</a>
    ```

  - GOOD

    ```md
    [my link](https://www.example.com)
    ```

- Insert an image:
  - BAD

    ````r
    ```
    knitr::include_graphics("my_img.png")
    ```
    ````

  - GOOD

    ```md
    ![my img](my_img.png)
    ```

### Line breaks

To facilitate reviews, please make use of [semantic line breaks](https://sembr.org/) as much as possible.
This makes it easier to detect changes with git.

## Contributing a new blog post

The Epiverse-TRACE blog is a rather informal space for us to collectively share learnings and document events in the community. For example, we share practical information around development, code, and process.

As a rule of thumb: If you find it interesting to share, it most likely is.

### Before starting to write

You can [start a discussion](https://github.com/orgs/epiverse-trace/discussions/new?category=blog-post-ideas) if you have a blog idea you want more input on.
This way, others can weigh in on your ideas, propose additional directions, and possibly volunteer to collaborate with you.
The discussion will be automatically cross-posted to the `#github-discussions` channel on Slack.

### General guidance for writing blog posts

#### Scope

Try to keep your post focused concise and focus in a single issue.
If you feel your post is getting too long,
it is often a good idea to split it into several smaller posts linking back to one another.
This often gets more views.

The aforementioned `future post` issue can help you to define the exact scope of your post.

#### Posts as one part of the ecosystem

Blog posts should as much as possible be self-contained.
I.e., they should make sense on their own
and not require users to go read a lot of external links to understand your point.

However, our blog doesn't live in isolation from the rest of the community
and it is good practice to link back to other posts and other resources as much as possible.
If someone else already wrote on the topic you're treating or an adjacent topic, or if there are resources to go deeper in this topic,
you should most definitely link them back.
Practically speaking, there is no upper limit on the number of external links you can add.
The more the better.

When you mention other resources and the position of your post in the existing documentation ecosystem,
make sure your phrasing couldn't be taken as dismissive or disparaging.
Our posts aim at building up on others' work and lifting up other members of the community.

This is in line with our [community values](https://data.org/news/epiverse-trace-a-values-based-approach-to-open-source-ecosystems/),
where we committed to **reciprocity**.

#### Tone and language

We don't require a formal tone in posts.
Feel free to adopt everyday vocabulary.

You should however ensure that your posts are always respectful of everybody's work,
and everybody's experience, as describe in our Code of Conduct.
In particular, we are paying extra attention to avoid dismissive or demotivating language, such as "obvious", "just", "straightforward", etc.
The "alex" GitHub Actions workflow can help you detect and fix such occurrences of demotivating language.

#### Step by step

To make contributing a blog post accessible, we outline an exact step by step guide below. We assume you are starting from an up to date `main` branch - so do not forget to pull the latest changes before starting with the following steps (e.g., `git pull origin`).

1. Create a branch for the blog post (e.g., `git checkout -b title-blog`).
2. Create a folder for your blog post under `posts/` (e.g., `posts/title-blog`).
3. Add a `index.qmd` file in the folder from point 2 (e.g., `posts/title-blog/index.qmd`). You can create your blog post in this file. Optionally add an `index.bib` in that same folder.
4. Commit and push changes to remote.
5. Create [pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request) and [request reviews](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/requesting-a-pull-request-review).
6. Request at least one review and [work through discussion points](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/about-pull-request-reviews), until the pull request gets approved.
7. The post gets merged after final checks [by one of the code owners](./CODEOWNERS).

If you want to get a DOI for your blog post, please add the `DOI` category (case sensitive).

#### Scheduled posts

We support publishing a blog at a specific date using a [Merge Schedule](https://github.com/gr2m/merge-schedule-action). To enable a scheduled post, please add the following to the original post in the pull request:

```md
/schedule YYYY-MM-DDTHH:MM:SS

/schedule 2025-01-01T08:00
```

The [scheduling functions on UTC time](https://www.timeanddate.com/worldclock/timezone/utc).

### After the post is published

Once your post is published, we already have some systems in place to try and advertise it in the community:

- it is automatically shared on [R-bloggers](https://www.r-bloggers.com/)
- it is automatically shared on [R-weekly](https://rweekly.org/),
  which can often result in it also being discussed in the [R-weekly podcast](https://rweekly.fireside.fm/).
  Keep an eye on their social media account to see if your post is mentioned: [twitter](https://twitter.com/theRcast)

You should also get in touch with the current week's curator of our [Epiverse-TRACE twitter account](https://twitter.com/Epiverse_TRACE/),
possibly with a short summary of your post they can use.

If you added the DOI category, you can find the DOI using [our Rogue Scholar index](https://rogue-scholar.org/blogs/epiverse_trace). You can add the DOI as metadata to your post by adding `doi: '<doi>'` to your post metadata (see [an example here](https://github.com/epiverse-trace/epiverse-trace.github.io/blob/e63c51b406409eb5e1bf9fc9201606793c3dd7d4/posts/parent-class/index.qmd#L7C1-L8C1).

## Contributing slides from a presentation

Slides from presentation can be added in the `slides/` folder.
Alongside the pdf of your slides, please add an `index.qmd` with the following recommended sections:

- Schedule if the event includes multiple presenters and/or multiple presentations
- The slides in an iframe:
  - For slides in 16:9 format:

  ````
  ```{=html}
  <iframe width="780" height="438.75" src="slides.pdf" title="slides from event"></iframe>
  ```
  ````

  - For slides in 4:3 format:

  ````
  ```{=html}
  <iframe width="780" height="500" src="slides.pdf" title="slides from event"></iframe>
  ```
  ````

- A list of questions asked during the presentation and a short answer,
  especially if you didn't have time to answer all questions live
- A link to the recording if available

## Adding new packages to the hexwall

Packages on the hexwall are automatically pulled from the list in
`_data/epiverse_pkgs.csv`. New packages can be added by submitting a PR editing
this file.
The package logos are fetched from
<https://github.com/epiverse-trace/hex-stickers>.
