# Trade_Engine_Demo
It is a Jupyter Notebook which demonstrates a trading engine architected to conduct back-testing and paper-trading of portfolios or individual securities. It is designed to support AI architected Trading Strategies, Classical Signal based algorithms, a variety of walk-forward analysis, ensemble of AI and Non-AI trading signals.

## Main features:
   - Perform backtests for a single trade strategy or a portfolio of trade strategies
   - Support different kinds of backtests and optimizations of hyper-parameters per trade strategy
   - Analysis of out-of-sample performance for trade strategies and/or portfolio
   - Support Technical Analysis, as well as AI Based algorithms to model all actions in a trade, that is:
      - Enter, Exit, Stop-Loss, Trail-Stop-Loss, Combine Stop & Trail Stop Loss, Position Sizesing
   - Support ensemble models for any trade action in a Trade Strategy
   - Support mixing Technical Analysis and AI Based Models in ensembles
   - Ability to re-fit AI models during a backtest
   - A variety of backtests, including: regular backtests, Walk-Forward-Analysis (WFA) re-fitting AI models, Slide Window and WFA, etc. 
      - See Jupypter Notebook demo for detailed explanations and examples of the different types of backtests 
   - Support persisting all information to execute a backtest in a Relational Database, as well as the results

## Execution Instructions

   1. The trade engine demo is a container application, and it requires the user to have Docker installed ( https://www.docker.com/products/docker-desktop )
   2. Download from this repository the file: docker-compose.yml
   3. Open a bash shell or power-shell and change to the directory where the yml file was downloaded
   4. Run the following command to start:
      - docker-compose up
      <br>
      - Docker-Compose will execute the following actions as instructed in the docker-compose.yml file:
        1. Download two images from Docker Hub, one for the database, and another for the Jupyter Notebook pre-configured environment
        2. asdf
