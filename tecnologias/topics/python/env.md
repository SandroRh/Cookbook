# Start Guide

Create .env file in root directory

    MY_ENV_VAR="This is my env var content."

Install dotenv

    pip install python-dotenv

Use

    import os
    from dotenv import load_dotenv

    load_dotenv()

    MY_ENV_VAR = os.getenv('MY_ENV_VAR')