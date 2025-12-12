# TradingView Altermative - Explore TakeProfit / Indie

If you've been using TradingView for chart analysis and started feeling limited by Pine Script, or you're simply looking for an alternative to TradingView with more flexibility, this guide is for you. We'll walk through what Indie is, how it works, and how to create your first custom indicator without any prior programming experience.

## What Is Indie and Why Should Traders Care?

Indie is a programming language designed specifically for building trading indicators. It runs natively on the TakeProfit platform, which serves as a charting and technical analysis tool for forex, crypto, and stock traders.

The key difference from other scripting languages: Indie is based on Python syntax. If you've ever written even a simple Python script or taken an intro programming course, you'll recognize the structure immediately. If you haven't—don't worry. The learning curve is gentler than most alternatives on the market.

All built-in indicators on TakeProfit are actually written in Indie. This means you're using the same tool that powers the platform's core functionality when you create custom indicators.

## Why Consider a TradingView Alternative?

Before diving into the technical details, let's address why traders are actively searching for alternatives to TradingView. Based on community feedback and user reviews, several issues consistently surface.

**Subscription complexity.** Many users report difficulties with automatic renewals, cancellation processes, and unexpected charges. TakeProfit takes a different approach with straightforward pricing: a free tier with basic functionality, and a single paid plan at $20/month or $100/year that includes all features.

**Alert limitations.** TradingView has implemented caps on alert frequency even for premium users. This affects traders who rely on automated notifications for their trading strategies. TakeProfit doesn't impose artificial throttling on alerts.

**Scripting restrictions.** Pine Script users often mention backward compatibility problems—scripts that worked yesterday suddenly break after platform updates. TakeProfit automatically upgrades scripts to the latest version while preserving backward compatibility whenever possible.

**Publishing barriers.** On TradingView, free users cannot publish indicators for the community. On TakeProfit, anyone can publish indicators regardless of their subscription status.

## Getting Started: The Basics You Need to Know

Let's cover the foundational concepts before you write your first indicator.

### The Entry Point

Every Indie indicator has a Main function that serves as the entry point. Think of it as the starting line: when the platform runs your indicator, it begins here. This function gets called for every candle on the chart, from left to right, and continues to update on each real-time tick for the most recent candle.

### Working with Price Data

Your indicator has access to all standard OHLCV data—open, high, low, close, and volume. You reference these values using a simple bracket notation where zero represents the current (most recent) candle. An offset of 1 gives you the previous candle, 2 gives you two candles back, and so on.

This time-series approach is consistent throughout Indie. Once you understand this pattern, you can apply it to any calculation.

### The Algorithm Library

Indie comes with a library of ready-to-use technical analysis algorithms. The documentation lists implementations for all major indicators. Here's a partial list of what's available:

**Trend indicators:** Simple Moving Average, Exponential Moving Average, Weighted Moving Average, Volume Weighted Moving Average

**Momentum indicators:** Relative Strength Index, MACD, Stochastic, Rate of Change, Commodity Channel Index, True Strength Index

**Volatility indicators:** Bollinger Bands, Average True Range, Standard Deviation

**Other tools:** Parabolic SAR, Supertrend, Donchian Channels, Linear Regression, Pivot High/Low detection

Each algorithm follows the same usage pattern—you create a new instance with the required parameters, and it returns a time series you can use in your calculations.

## Creating Your First Indicator: Step by Step

Here's how to get from zero to a working indicator on your chart.

### Step 1: Access the Code Editor

On the TakeProfit platform, add the Indicators Code Editor widget to your workspace. You'll find it under the widgets menu. Open a chart for the instrument you want to test with.

### Step 2: Understand the Structure

Every Indie script starts with a version comment that tells the platform which language version to use. After that, you import the components you need—the indicator decorator, any algorithms, and visualization tools.

The indicator decorator provides metadata: the title that appears on your chart and whether the indicator should overlay the main price chart or appear in a separate pane below.

### Step 3: Write Your Logic

The Main function contains your calculation logic. At its simplest, you might just return a moving average value. More complex indicators combine multiple calculations, compare values across timeframes, or apply conditional logic to generate signals.

### Step 4: Deploy and Test

Click "Add to Chart" and your indicator appears immediately. You'll see the results on historical data and watch it update in real-time as new price data comes in.

### Step 5: Add Customizable Parameters

Once your basic logic works, you can add input parameters that users can adjust without editing the source. These appear in a Settings panel accessible by right-clicking the indicator. You define the parameter type (integer, float, boolean, string), set default values, and optionally specify minimum and maximum constraints.

## Visualization Options

Indie provides several ways to display your indicator data on charts.

**Line plots** are the most common—useful for moving averages, oscillators, and any continuous value. You can customize color, style, and width.

**Columns and histograms** work well for volume-type data or indicators like MACD that traditionally display as bar charts.

**Markers** let you place symbols at specific points—useful for highlighting crossovers, divergences, or signal conditions.

**Dynamic coloring** allows the plot color to change based on conditions. A moving average might show green when price is above it and red when below.

**Fills** shade the area between two lines—commonly used for Bollinger Bands or to highlight overbought/oversold zones on oscillators.

**Labels and annotations** provide text-based information directly on the chart, useful for displaying calculated values or signal names.

## Multi-Timeframe Analysis

One of Indie's powerful features is the ability to request data from timeframes different from your current chart. This opens up strategies that combine signals across multiple time horizons.

For example, you might create an indicator that checks trend direction on hourly and daily charts while you trade on 15-minute candles. The platform handles the data synchronization—you simply specify which timeframe you want and write your calculation logic.

## Tips for Beginners

**Start simple.** Your first indicator doesn't need to be sophisticated. Even recreating a basic moving average teaches you the workflow and core concepts.

**Read the built-in indicator source code.** All of TakeProfit's standard indicators are written in Indie and their source code is available. Study how they handle edge cases and structure their logic.

**Use the validation tool.** Indie includes a code validator that catches syntax errors and compatibility issues before you deploy. Run your code through this check early and often.

**Experiment with parameters.** Once you have a working indicator, make values adjustable instead of hard-coded. This lets you test different settings quickly without editing source code.

**Check the algorithm library first.** Before writing a calculation from scratch, check if it already exists in the standard library. Using built-in algorithms is more efficient and ensures consistent calculations.

## What You Can Build

The range of possible indicators is broad. Here are some categories to consider:

**Enhanced classics.** Take a standard indicator and add features—dynamic coloring based on trend, multi-period comparisons, or additional smoothing options.

**Composite indicators.** Combine multiple algorithms into a single view. A dashboard that shows RSI, MACD, and moving average status simultaneously.

**Custom signals.** Define your specific entry and exit conditions and visualize them with markers on the chart.

**Market structure tools.** Identify swing highs and lows, support and resistance levels, or trend channels automatically.

**Cross-asset analysis.** Compare correlations between instruments or create relative strength indicators.

## Moving Forward

This guide covered the concepts without diving into specific syntax—that's intentional. The goal was to help you understand what's possible and how the pieces fit together before you start writing actual code.

When you're ready to write your first indicator, the TakeProfit documentation provides complete examples you can modify. Start with the Quick Start guide, which walks through progressively complex examples with full explanations.

The learning path typically looks like this: copy and modify existing examples, then understand what each part does, then create variations, and finally build original indicators from scratch.

## Key Takeaways

Indie is a Python-based language built specifically for creating trading indicators. It runs on TakeProfit, offering an alternative charting platform for traders who want more control over their technical analysis tools.

The platform addresses common frustrations with other charting solutions—transparent pricing, no artificial limits on features, stable scripting environment, and the ability for any user to create and share indicators.

For beginners, the combination of familiar Python syntax, a comprehensive algorithm library, and immediate visual feedback on charts makes custom indicator development accessible. You don't need to be a programmer to get started—just a willingness to learn and experiment.

The best way forward is to open the code editor and try modifying an existing indicator. Change a parameter value, see what happens on the chart, and build from there.
