<p align="center">
  <img width="400" src="https://user-images.githubusercontent.com/4658208/60469862-2e40bf00-9c2c-11e9-87f7-afe164648de4.png" />
</p>
<h1 align="center">waka-box-fast</h1>
<p align="center">Update a pinned gist to contain your weekly WakaTime stats</p>

---

> [!IMPORTANT]
> This action is a fork of <https://github.com/matchai/waka-box>, using bun in place of nodejs.
>
> Named `waka-box-fast` because it's easier to use than the original `waka-box` action.
> I removed redundant dependencies and updated the usage to be more straightforward.
>
> 📌✨ For more pinned-gist projects like this one, check out: <https://github.com/matchai/awesome-pinned-gists>

## Prep work

1. Create a new public GitHub Gist (<https://gist.github.com/>).
1. Create a token with the `gist` scope and copy it (<https://github.com/settings/tokens/new>).
1. (Optional) Create a WakaTime account (<https://wakatime.com/signup>).
1. In your WakaTime profile settings (<https://wakatime.com/settings/profile>), ensure `Display languages, editors, os, categories publicly` is checked.
1. In your account settings, copy the existing WakaTime API Key (<https://wakatime.com/settings/api-key>).

## Usage

- [Use fork](#use-fork)
- [Manually create workflow](#manually-create-workflow)
- [Inputs](#inputs)

### Use fork

> You will use the master branch of this repo, which is the latest version of this action.

1. Fork this repo.
1. Go to the repo **Settings > Secrets and variables > Actions > Repository secrets**.
1. Add the following secrets:

   - `GIST_ID`

     The ID portion from your gist url: `https://gist.github.com/g1eny0ung/`**`a69405549d813107fd0bba15815cbaa6`**.

   - `GH_TOKEN`

     The GitHub token generated above.

   - `WAKATIME_API_KEY`

     The API key for your WakaTime account.

   - `WAKATIME_BASE_URL` (Optional)

     Use `https://wakatime.com/api/v1` by default. If you are using a WakaTime-compatible backend (e.g. Wakapi), change this to the corresponding base URL.

### Manually create workflow

1. Create a new workflow in your repo `.github/workflows/waka-box-fast.yml`.
1. Add the following code to the workflow:

   ```yml
   name: Update gist with WakaTime stats
   on:
     # You can change the cron schedule here based on your needs. This will run daily at midnight.
     schedule:
       - cron: '0 0 * * *'
     # Manual triggers with workflow_dispatch
     workflow_dispatch:
   jobs:
     update-gist:
       runs-on: ubuntu-latest
       steps:
         - name: Update gist
           uses: g1eny0ung/waka-box@v6
           # with:
           #  gist-name: Weekly Wakatime Stats
           env:
             GIST_ID: ${{ secrets.GIST_ID }}
             GH_TOKEN: ${{ secrets.GH_TOKEN }}
             WAKATIME_API_KEY: ${{ secrets.WAKATIME_API_KEY }}
             # WAKATIME_BASE_URL: ${{ secrets.WAKATIME_BASE_URL }}
   ```

1. Add related secrets described above.

### Inputs

| Name        | Description           | Default                           | Required | Example                 |
| ----------- | --------------------- | --------------------------------- | -------- | ----------------------- |
| `gist-name` | The name of the gist. | `📊 Weekly development breakdown` | `false`  | `Weekly Wakatime Stats` |

## Credits

This action was originally created by [matchai](https://github.com/matchai).
