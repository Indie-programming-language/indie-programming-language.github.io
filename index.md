---
title: Indie — the Python-based scripting language for TakeProfit indicators
description: >-
  Unofficial community reference for Indie, the Python-based scripting
  language used to build custom indicators on the TakeProfit charting
  platform: language guide, built-in algorithms, and drawing API.
hide_h1: true
---

<section class="hero">
  <span class="hero-eyebrow">Community-maintained · not officially affiliated with TakeProfit</span>
  <h1>A Python-based language for <span class="accent">trading indicators</span></h1>
  <p class="hero-sub">
    Indie runs natively on the <a href="https://takeprofit.com/" target="_blank" rel="noopener">TakeProfit</a>
    charting platform. It reuses familiar Python syntax and adds decorators, series
    types, and a drawing API built specifically for financial charts — so every
    built-in indicator on the platform is, in fact, written in Indie.
  </p>
  <div class="hero-cta">
    <a class="btn btn-primary" href="https://takeprofit.com/" target="_blank" rel="noopener">Open TakeProfit</a>
    <a class="btn btn-ghost" href="{{ site.baseurl }}/docs/indie-language-reference.html">Read the language reference</a>
  </div>
  <p class="hero-meta">Free to start · no installation, indicators run in the browser</p>
</section>

<section class="section">
  <div class="section-head">
    <span class="section-eyebrow">Why Indie</span>
    <h2>Python syntax, built for markets</h2>
    <p>Everything you'd expect from a modern scripting language, plus the primitives financial analysis actually needs.</p>
  </div>
  <div class="grid grid-3">
    <div class="card">
      <div class="card-icon">Py</div>
      <h3>Familiar syntax</h3>
      <p>If you've written basic Python, the structure — functions, decorators, type hints — will feel immediately familiar. No new language to learn from scratch.</p>
    </div>
    <div class="card">
      <div class="card-icon">Σ</div>
      <h3>Series-first data model</h3>
      <p><code>Series[T]</code> and <code>MutSeries[T]</code> model time series data directly, with built-in handling for lookback, NaN values, and streaming updates.</p>
    </div>
    <div class="card">
      <div class="card-icon">⌗</div>
      <h3>Drawing API</h3>
      <p>Place labels and lines at exact price/time coordinates, or anchor persistent overlays to a corner of the chart — without touching a rendering engine.</p>
    </div>
    <div class="card">
      <div class="card-icon">⚙</div>
      <h3>Parameter decorators</h3>
      <p><code>@param.int</code>, <code>@param.float</code>, <code>@param.bool</code> turn function arguments into user-configurable indicator settings automatically.</p>
    </div>
    <div class="card">
      <div class="card-icon">⇄</div>
      <h3>Multi-instrument context</h3>
      <p><code>@sec_context</code> lets an indicator request data from another symbol or timeframe alongside the chart's own series.</p>
    </div>
    <div class="card">
      <div class="card-icon">▤</div>
      <h3>Built-in algorithms</h3>
      <p>A standard library of moving averages, crossovers, and other reusable <code>@algorithm</code> building blocks — no need to reimplement the basics.</p>
    </div>
  </div>
</section>

<section class="section">
  <div class="code-showcase">
    <div class="code-showcase-copy">
      <span class="section-eyebrow">Less boilerplate</span>
      <h2>A full indicator in a few lines</h2>
      <p>
        A parameterized indicator is a decorated function, not a class hierarchy.
        The <code>@indicator</code> and <code>@param.*</code> decorators handle
        registration and UI controls; you write the logic.
      </p>
      <a class="btn btn-ghost" href="{{ site.baseurl }}/docs/indie-language-reference.html">Browse the full reference →</a>
    </div>
    <div>
      <pre><code class="language-python">@indicator('Price Above MA')
@param.int('length', default=20)
def Main(self, length):
    ma = Sma.new(self.close, length)
    return self.close[0] > ma[0]</code></pre>
    </div>
  </div>
</section>

<section class="section">
  <div class="code-showcase">
    <div>
      <pre><code class="language-python">@indicator('Trend Break Marker', overlay_main_pane=True)
def Main(self):
    if breakout_detected(self):
        self.chart.draw(LabelAbs(
            f"Breakout: {self.close[0]:.2f}",
            AbsolutePosition(self.time[0], self.high[0]),
        ))

        self.chart.draw(LineSegment(
            AbsolutePosition(self.time[10], self.low[10]),
            AbsolutePosition(self.time[0], self.high[0]),
            extend_type=extend_type.RIGHT,
        ))</code></pre>
    </div>
    <div class="code-showcase-copy">
      <span class="section-eyebrow">Chart-native output</span>
      <h2>Draw directly on the chart</h2>
      <p>
        <code>AbsolutePosition</code> pins a label or line to an exact
        price/time coordinate; <code>extend_type</code> projects a line
        segment forward so trend markers stay visible as new bars arrive.
      </p>
      <a class="btn btn-ghost" href="{{ site.baseurl }}/docs/indie-language-reference.html">See the drawing API →</a>
    </div>
  </div>
</section>

<section class="section">
  <div class="section-head">
    <span class="section-eyebrow">Guides</span>
    <h2>Start reading</h2>
    <p>Community-written guides that go deeper into specific parts of the language and platform.</p>
  </div>
  <div class="grid grid-3">
    <div class="card">
      <h3><a href="{{ site.baseurl }}/docs/indie-language-reference.html">Language reference</a></h3>
      <p>The complete Indie syntax reference: data types, decorators, built-in algorithms, and the platform's alert system.</p>
    </div>
    <div class="card">
      <h3><a href="{{ site.baseurl }}/docs/tradingview-alternative.html">Coming from TradingView / Pine Script</a></h3>
      <p>What's different about Indie and TakeProfit if you're used to Pine Script, and how to write your first custom indicator.</p>
    </div>
    <div class="card">
      <h3><a href="{{ site.baseurl }}/docs/quantitative-look-at-linear-regression-projections-universal-forecast-funnel.html">Linear regression projections</a></h3>
      <p>A quantitative comparison of OLS regression projections against a simple moving average — lag, noise, and where each one breaks down.</p>
    </div>
  </div>
</section>

<div class="cta-band">
  <h2>Build your first indicator</h2>
  <p>TakeProfit is free to start — indicators run in the browser, no local setup required.</p>
  <div class="hero-cta">
    <a class="btn btn-primary" href="https://takeprofit.com/" target="_blank" rel="noopener">Open TakeProfit</a>
    <a class="btn btn-ghost" href="https://github.com/Indie-programming-language/indie-programming-language.github.io" target="_blank" rel="noopener">Browse this project on GitHub</a>
  </div>
</div>
