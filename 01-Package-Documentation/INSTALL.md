# Installing the statwise R Package

The `statwise` package is hosted in a private GitHub repository.
Follow the steps below to obtain access and install the package in R.

## 1. Create a GitHub Account

If you do not already have a GitHub account, create one at GitHub.

Send your GitHub username to the package administrator so that you can be granted **Read access** to the `statwise` repository.

Once you receive the GitHub invitation, accept it before continuing.

## 2. Install Git

Git must be installed on your computer.

After installing Git, restart RStudio and verify that R can find Git:

```r
Sys.which("git")
```

A valid Git installation should return a path to `git.exe`.

## 3. Install Required R Packages

Run:

```r
install.packages(c("remotes", "gitcreds"))
```

These packages are only required for installing and updating `statwise` from the private GitHub repository.

## 4. Create a GitHub Personal Access Token

Log in to your GitHub account and navigate to:

**Settings → Developer settings → Personal access tokens → Tokens (classic)**

Select:

**Generate new token → Generate new token (classic)**

Give the token a descriptive name, such as:

```text
statwise package
```

Under **Select scopes**, select:

```text
repo
```

The `repo` scope is required to access the private repository.

Generate the token and copy it immediately. GitHub will not display the token again.

**Do not share your token with anyone.**

## 5. Save Your GitHub Credentials

In R, run:

```r
gitcreds::gitcreds_set()
```

Paste your Personal Access Token when prompted.

If existing GitHub credentials are found, select:

```text
2: Replace these credentials
```

Then paste the new token.

You can verify that credentials are stored by running:

```r
gitcreds::gitcreds_get()
```

The token itself will remain hidden.

## 6. Install statwise

Run:

```r
remotes::install_github(
  "Shaina-Biostats/statwise",
  force = TRUE,
  upgrade = "never"
)
```

## 7. Load statwise

After installation, load the package normally:

```r
library(statwise)
```

The package is now ready to use.

## Updating statwise

When a new version of `statwise` is available, reinstall it using:

```r
remotes::install_github(
  "Shaina-Biostats/statwise",
  force = TRUE,
  upgrade = "never"
)
```

Then load it as usual:

```r
library(statwise)
```

## Troubleshooting

If installation returns:

```text
HTTP error 404
Not Found
```

verify that:

- You accepted the GitHub repository invitation.
- You are using the GitHub account that was granted access.
- Your Personal Access Token includes the `repo` scope.
- Your GitHub credentials have been saved using `gitcreds::gitcreds_set()`.

To check whether GitHub credentials are available:

```r
gitcreds::gitcreds_get()
```
