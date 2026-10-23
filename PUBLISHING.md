# Publishing this project

## Use GitHub in your browser

1. Extract `Splunk_Suricata_SOC_Lab_GitHub.zip` on your computer.
2. Open the extracted `splunk-suricata-soc-lab` folder and review its contents.
3. Sign in to GitHub and create a repository named `splunk-suricata-soc-lab`.
4. Choose Public if you want recruiters to view it. Use this description:
   > SOC home lab using Splunk and Suricata to detect Windows logon failures and correlate SSH authentication with network telemetry.
5. Upload the **contents inside** the extracted folder to the repository root, preserving the folders. Do not upload only the ZIP file.
6. Commit with the message `Add validated Splunk and Suricata SOC lab`.
7. Open the repository README and check the screenshots, report and inventory links.
8. Pin the repository to your GitHub profile and add its link to your portfolio.

The repository root must contain `README.md`, `reports/`, `screenshots/` and the other folders directly. An extra enclosing folder prevents GitHub from showing the README on the repository home page.

## Optional Git command line method

Create an empty repository in GitHub first. Run these commands from **inside the extracted project folder**. Replace `YOUR_GITHUB_USERNAME` before running the remote command.

```bash
git init
git add .
git commit -m "Add validated Splunk and Suricata SOC lab"
git branch -M main
git remote add origin https://github.com/YOUR_GITHUB_USERNAME/splunk-suricata-soc-lab.git
git push -u origin main
```

These commands assume the remote repository is empty. If a remote already contains files, clone it first and copy the package contents into that clone rather than overwriting its history.

## Suggested repository topics

`splunk` `suricata` `soc` `siem` `cybersecurity` `homelab` `log-analysis` `detection-engineering`

## Publication review

The package includes the author's name, lab usernames and private lab IPs as part of the evidence. Review these before making the repository public. No passwords, private SSH keys or authentication tokens were intentionally included. Retain the lab scope statement and the limitations alongside the results.

The report and workbook are the completed deliverables. Presentation slides were not bundled because the earlier slide snapshot predates the final SSH investigation. No dashboard XML or JSON export was supplied; the package includes its screenshots and selected panel searches instead.
