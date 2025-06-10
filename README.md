# Selenium on Google Colab

Running Selenium for web automation in environments like Google Colab can often be a real pain. It typically involves manually installing a browser, downloading the correct `chromedriver`, and then configuring everything just right. This notebook was created to eliminate that headache, providing a fully automated setup that acts as your perfect starting point for using Selenium directly within Google Colab.

## Features

This notebook automates everything, giving you:

* **Automated Google Chrome Installation:** No more manually downloading or installing a browser.

* **Intelligent ChromeDriver Management:** The notebook automatically detects your Chrome version and grabs the perfectly matched `chromedriver`, saving you from version compatibility nightmares.

* **Headless Browser Configuration:** Chrome runs invisibly in the background, which is essential for cloud environments like Colab that don't have a graphical display.

* **Dependency Handling:** All necessary system and Python libraries are installed for you.

## Getting Started
Ready to jump in? Here's how to run this notebook:

1. **Open in Google Colab:** Click on the `selenium_colab_example.ipynb` file in this GitHub repository, then hit the "Open in Colab" button at the top.

2. **Run All Cells:** Once the notebook loads, simply go to `Runtime` in the Colab menu and select `Run all`.

That's it! The notebook handles the rest, setting up your Selenium environment automatically.

## Code Overview
### 1. Environment Setup (Shell Commands)
This initial block uses Linux shell commands to prepare your Colab environment:
```bash
%%shell
sudo apt -y update
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo apt install ./google-chrome-stable_current_amd64.deb
pip install selenium chromedriver_autoinstaller
```
These commands update your system's package lists, download the Google Chrome browser, install it (automatically pulling in any needed system dependencies), and finally install the essential Python libraries: Selenium (the automation framework) and chromedriver_autoinstaller (to handle the tricky part of getting the right chromedriver).

### 2. Selenium WebDriver Configuration (Python)
Once the environment is ready, this Python code sets up Selenium itself:

```Python
from selenium import webdriver
import chromedriver_autoinstaller

chromedriver_autoinstaller.install()

chrome_options = webdriver.ChromeOptions()
chrome_options.add_argument('--headless') #Do not remove the options
chrome_options.add_argument('--no-sandbox')
chrome_options.add_argument('--disable-dev-shm-usage')
driver = webdriver.Chrome(options=chrome_options)

```
- chromedriver_autoinstaller.install() ensures the correct chromedriver is in place, allowing Selenium to communicate with Chrome.

- webdriver.ChromeOptions() sets up special configurations for Chrome, primarily —headless (to run without a visible window, crucial for Colab), —no-sandbox, and —disable-dev-shm-usage (to prevent common issues in virtual environments).

## License
This project is licensed under the MIT License
