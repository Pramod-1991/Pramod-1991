//@version=5
indicator("Accurate Buy/Sell Signals", overlay=true)

// Define minimum volume threshold
minVolume = input(10000000, title="Minimum Volume for Signal")

// Check if the candle is flat (no upper or lower wick)
isFlatCandle = (high == low)

// Buy condition: Flat candle, volume > 10M, bullish candle (close > open)
buyCondition = isFlatCandle and (volume > minVolume) and (close > open)

// Sell condition: Flat candle, volume > 10M, bearish candle (close < open)
sellCondition = isFlatCandle and (volume > minVolume) and (close < open)

// Plot Buy Signal
if (buyCondition)
    label.new(bar_index, low, text="BUY", style=label.style_labelup, color=color.green, textcolor=color.white)

// Plot Sell Signal
if (sellCondition)
    label.new(bar_index, high, text="SELL", style=label.style_labeldown, color=color.red, textcolor=color.white)

\
