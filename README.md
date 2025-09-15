 (cd "$(git rev-parse --show-toplevel)" && git apply --3way <<'EOF' 
diff --git a/README.md b/README.md
index a39fb96faa782b647388d10791d61798421e7cc2..639f637409e0f88af1778e647d2ce4d13e201e56 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,43 @@
-# forexbot
+# ForexBot
+
+ForexBot is a sample cTrader cBot showcasing 1% risk management and price action entries (pin bars and engulfing candles) for EURUSD, GBPUSD and USDCAD on the M30 and H1 timeframes.
+
+## Import into cTrader Automate
+1. Open **cTrader** and go to the **Automate** section.
+2. Choose **Create > Import cBot** and select `src/Bots/ForexBot.algo`.
+3. Build the project; it should compile without errors.
+
+## Parameters
+After importing, select the cBot and adjust parameters in the **Parameters** panel. Defaults:
+- `RiskPercent` = 1.0
+- `TargetRR` = 2.0
+- `UseEMA200Filter` = true
+- `EMAPeriod` = 200
+- `MinPinBarWickToBody` = 2.0
+- `MinEngulfingBodyFactor` = 1.2
+- `MaxEntryDistanceToZonePips` = 8
+- `MaxSpreadPips` = 2.0
+- `AvoidHighImpactNews` = false
+- `ForbiddenHours` = "21-23"
+- `Timeframe` = "H1"
+- `EnableTrailing` = true
+
+## Backtesting
+1. In **cTrader Automate**, open **Backtesting**.
+2. Select one of the pairs (EURUSD, GBPUSD or USDCAD) and timeframe (M30 or H1).
+3. Choose the start date (2017-01-01) to present and run the test.
+4. Repeat for the other pairs and timeframe.
+
+### Validation checklist
+- Spread must be below the configured `MaxSpreadPips`.
+- Server time must not fall within `ForbiddenHours`.
+- If `UseEMA200Filter` is true, only longs above and shorts below EMA200 are taken.
+
+## Tests
+Unit tests for risk management reside in `tests/RiskTests.cs`. Run them with:
+
+```bash
+dotnet test
+```
+
+(Ensure .NET SDK is installed.)
 
EOF
)
Teste de alteração na branch branchbot
).
Teste de alteração na branch branchbot
