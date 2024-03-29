# Trade_Engine_Demo
It is a Jupyter Notebook which demonstrates a trading engine architected to conduct back-testing and paper-trading of portfolios or individual securities. It is designed to support AI architected Trading Strategies, Classical Signal based algorithms, a variety of walk-forward analysis, ensemble of AI and Non-AI trading signals.

## Main features:
   - Perform backtests for a single trade strategy or a portfolio of trade strategies
   - Support different kinds of backtests and optimizations of hyper-parameters per trade strategy
   - Analysis of out-of-sample performance for trade strategies and/or portfolio
   - Support Technical Analysis, as well as AI Based algorithms to model all actions in a trade, that is:
      - Enter, Exit, Stop-Loss, Trail-Stop-Loss, Combine Stop & Trail Stop Loss, Position Sizes 
   - Support ensemble models for any trade action in a Trade Strategy
   - Support mixing Technical Analysis and AI Based Models in ensembles
   - Ability to re-fit AI models during a backtest
   - A variety of backtests, including: regular backtests, Walk-Forward-Analysis (WFA) re-fitting AI models, Slide Window and WFA, etc. 
      - See the loaded trade engine Jupypter Notebook for detailed explanations and examples of the different types of backtests 
   - Support persisting all information to execute a backtest in a Relational Database, as well as the results
   - Support persisting all trade strategies, portfolios, and backtests to MongoDB - ability to save thousands of trade strategies and portfolios
   - Caching all Market data in MongoDB, and ability to freeze/version the market data associated with a given test
   - Caching of all fitted AI Models in local file system as well as MongoDB
   - Generic/pluggable rebalance methodology for timing and methodology

## Trade Engine Demo Jupyter Notebook

   - URL:  https://github.com/zambranag777/Research_Projects/blob/main/TradeEngine_Demo.ipynb
   - Note: the URL is for viewing purpose only, but not for executing; for executing follow the instructions below.
   - All examples and trade strategies are for demonstration only.
        - By designed hyper parameters were selected randomly.
        - Backtest periods were selected across different years and market regimes to highlight how strategies might work one year, some period, and then behave differently in others.
        - For trade strategies with AI models, the training and validation periods were varied across the backtests examples.
   - A summary description of each of the backtest examples is provided, and a detail description of each backtest at the start of the backtest
   - The design goal was clarity over compactness, thus each backtest does not depend on previous cells, only in the required imports, detailed in the notebook
   - The examples are defined in order of complexity, more features and variatons added in order of exposition

## Execution Instructions

   1. The trade engine demo is a container application, and it requires the user to have Docker installed ( https://www.docker.com/products/docker-desktop )
   2. Configure the minimum OS resources required to run the different types of backtests in the demo:
      - Click Settings/Resources in Docker Desktop and update
      - Note: Most of the examples, except for the Sliding Window ones, can probably execute with 1 CPU Core and 2GB of memory. It is the portfolios with hundreds of trade strategies and AI models that are more resource intensive.
      
   | Example Type           | # Trade Strategies per backtest | Backtest Type   |  CPU Cores  |  Memory  |  Swap  | Disk image size |
   | ---------------------- | ------------------ | --------------- | ----------- | -------- | ------ | --------------- |
   | Single Trade Strategy  |    1               | regular         |      2      |   4 GB   |  2 GB  |      10 GB      |
   | Portfolio              |    3 to mid 200    | regular         |      4      |   8 GB   |  2 GB  |      10 GB      |
   | Walk Forward Analysis  |    18 to 66        | WFA Backtest    |      4      |   8 GB   |  2 GB  |      10 GB      |
   | Sliding Window & WFA   |    33 to mid 600s  | SW-WFA Backtest |      6      |  12 GB   |  2 GB  |      10 GB      |
   
   3. Download from this repository the file: **docker-compose.yml**
      - Clone the project: git clone https://github.com/zambranag777/Trade_Engine_Demo
      - Or just download the docker-compose.yml file
   5. Open a bash shell or power-shell and change to the directory where the yml file was downloaded
   6. Run the following command to start:
      - **docker-compose up**
      - Docker-Compose will execute the following actions as instructed in the docker-compose.yml file:
         - Download two images from Docker Hub, one for the database, and another for the Jupyter Notebook pre-configured environment
         - Cache the images locally
         - Create two containers, one for the database, and the other for the Jupyter Notebook environment
         - Start both containers
   7. Execute the following command to verify the containers started successfully: (open another bash or power shell)
      - **docker ps**
      - There should be two entries in the output similar to these:
      
| CONTAINER ID| IMAGE                           |     COMMAND           |   CREATED  |  STATUS    |     PORTS            |      NAMES                   |
| ------------| ------------------------------- | ----------------------| -----------| ---------- | ---------------------| ---------------------------- |
| 9fc95325dc69|zambranag/ postgres-te-demo:latest| docker-entrypoint.s… | 7 hours ago| Up 7 hours| 0.0.0.0: 7778->5432/tcp|deployment- postgress_db_1   |
| c9ad96f46f8b|zambranag/ trade-engine:latest    | jupyter notebook --… | 7 hours ago| Up 7 hours| 0.0.0.0: 8880->8888/tcp|deployment- trade_engine_jn_1|

   7. Open a browser window and enter the following URL:
      - **http://127.0.0.1:8880/**
   8. Enter the following password to load the trade engine demo Jupyter Notebook: 
      - password: **easy**
      - It will take 5 to 20 seconds to load the notebook
   9. Follow the execution instructions in the notebook to run the example backtests
  10. Run the following command to stop the containers:
      - **docker-compose stop**

## Useful Docker Commands

   1. **docker stats**
      - Execute in a different bash or power shell while running a backtest to monitor the container resources
   2. Copy Excel files from container to local host:
      - Mac: **docker cp deployment_trade_engine_jn_1:Projects/Trade_Engine/JupyterNotebooks/. excel/**
      - Windows: **docker cp downloads_trade_engine_jn_1:Projects/Trade_Engine/JupyterNotebooks/. excel/**
      - the container naming convention is defaulted by the docker-host, might change, check with docker ps for the actual name
      - Command to copy backtest results to the local host
      - All the example backtests have a cell to save their results to Excel format, by default store in the directory where the notebook is running
      - These files get saved inside the docker container, and can be copy from the container to the local host for analysis in Excel

## 2022 Planned Features

   1. Cloud scalable version
   2. Storage of all assets in MongoDB and/or Relational Databases in AWS
   3. Support for additional Relational Databases
   4. Additional types of backtests
   5. Dynamic Portfolios 
   6. Stacked Portfolios
   7. Extendable rebalance logic
   8. 100% coverage via unit-tests and integration tests
   
## Feedback
zambranag@yahoo.com
