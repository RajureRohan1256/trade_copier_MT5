# 📈 MQL5 Trade Copier (File-Based) – Master/Slave System

A lightweight, file-based trade copier system for MetaTrader 5 written in MQL5.  
This project allows one MT5 terminal (Master) to control trading on another MT5 terminal (Slave) by writing and reading a `.bin` file.

---

## 🚀 Features

- ✅ Trade direction (Buy/Sell) copying  
- ✅ Copies Stop Loss (SL) and Take Profit (TP)  
- ✅ Ensures only one open trade per symbol  
- ✅ Built-in file locking for cross-terminal consistency  
- ✅ Simple to integrate and modify  
- ✅ Reverse direction, multi-symbol, and close sync ready (optional extensions)

---

## 🛠️ How It Works

**Master EA:**
- Writes trade instructions to a `.bin` file located in the **Common Files** directory.

**Slave EA:**
- Reads the `.bin` file.
- Opens a corresponding trade (BUY or SELL) with specified SL and TP.
- Only opens a new trade if a new timestamp is detected.
- Closes any previously opened position before copying the new one.

---

## 📁 Binary File Format (Master -> Slave)

| Field        | Type    | Description              |
|--------------|---------|--------------------------|
| direction    | `uchar` | 0 = Buy, 1 = Sell        |
| sl           | `double`| Stop Loss (price)        |
| tp           | `double`| Take Profit (price)      |
| timestamp    | `ulong` | Unique timestamp marker  |

**Note:** The file should be overwritten each time the Master places a new trade.

---

## 📦 Project Structure

