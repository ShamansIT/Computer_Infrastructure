# Automate Weather Data Collection

![Automate Weather Data Collection](https://openweather.co.uk/storage/app/uploads/public/217/_ac/cur/217_accuracy-and-quality-weather-data.png)

**by Serhii Spitsyn**

## Descriptions

This project automates the collection of weather data using a Bash script (`weather.sh`) and GitHub Actions. The script downloads the latest weather data from an external API and commits the data to the repository daily.

## Project Features

- **Daily Automation**: The weather data is automatically fetched every day at 10:00 AM UTC using GitHub Actions.
- **Manual Trigger**: The workflow can be manually triggered through the GitHub Actions tab.
- **Version Control**: The collected weather data is stored in `.json` files with unique timestamps.

## Prerequisites

- A GitHub repository with GitHub Actions enabled.
- A **Personal Access Token (PAT)** with `repo` permissions for pushing commits.

## Setup Instructions

### 1. Create the Workflow

Ensure the workflow file `weather-data.yml` is placed in `.github/workflows/`.

### 2. Configure Secrets

Add your Personal Access Token (PAT):

1. Navigate to your GitHub repository -> **Settings -> Secrets and variables -> Actions -> New repository secret**.
2. Add a new secret:
   - **Name:** `PAT_TOKEN`
   - **Value:** Your GitHub PAT with `repo` access.

## How It Works

1. **Bash Script (`weather.sh`):**

   - Downloads weather data from [Met Éireann API](https://prodapi.metweb.ie).
   - Saves the data as a JSON file with the current timestamp.

2. **GitHub Actions Workflow (`weather-data.yml`):**
   - Runs daily at 10:00 AM UTC.
   - Executes the `weather.sh` script.
   - Commits and pushes the collected data to the repository.

## Manual Trigger

To run the workflow manually:

1. Open the **Actions** tab in your GitHub repository.
2. Select the **Automate Weather Script** workflow.
3. Click **Run workflow**.

## Example Output

### JSON File Example

Exsample weather data file created by the script:

```json
  {
    "name": "Athenry",
    "temperature": "1",
    "symbol": "02n",
    "weatherDescription": "Fair",
    "text": "\"Fair\"",
    "windSpeed": "9",
    "windGust": "-",
    "cardinalWindDirection": "NE",
    "windDirection": 45,
    "humidity": "94",
    "rainfall": "0.0",
    "pressure": "1017",
    "dayName": "Thursday",
    "date": "02-01-2025",
    "reportTime": "00:00"
  }
```

## Troubleshooting

### Common Issues

1. **403 Error During `git push`:**

   - Ensure the PAT is correctly added as a secret (`PAT_TOKEN`).
   - Ensure the PAT has `repo` permissions for private repositories.

2. **Script Not Found Error:**
   - Verify the path to `weather.sh` in the workflow file (`data/weather/weather.sh`).

## Future Enhancements

- Add error handling for failed API requests.
- Implement notification (e.g., email or Slack) for workflow failures.
- Summarize the data and provide visualizations.

## Reference

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Met Éireann API](https://www.met.ie/)
- [GitHub REST API Documentation](https://docs.github.com/en/rest?apiVersion=2022-11-28)
- [Wget Manual](https://www.gnu.org/software/wget/manual/wget.html)
- [Classic SysAdmin: Understanding Linux File Permissions](https://www.linuxfoundation.org/blog/blog/classic-sysadmin-understanding-linux-file-permissions)

### Contribution to the project

Contributions are welcome! You can help improve the project by opening an issue or creating a pull request.

## Contact Information

- <serhii.spitsyn.ie@gmail.com>
- [GitHub](https://github.com/ShamansIT)
