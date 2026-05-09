How It Works
1. ESP32 goes into deep sleep
2. After 1 minutes, the internal RTC wakes up the ESP32
3. ESP32 executes code (e.g., update LCD, blink LED, log data)
4. Goes back to deep sleep until the next wake-up
Explanation
• RTC_DATA_ATTR int bootCount = 0;
→ Keeps the boot count even after deep sleep.
• esp_sleep_enable_timer_wakeup(TIME_TO_SLEEP * uS_TO_S_FACTOR);
→ Sets ESP32 to wake up every 1 minutes (600 seconds).
• lcd.print(bootCount);
→ Shows how many times ESP32 has woken up on the LCD.
• ESP32 enters deep sleep mode and will wake up automatically after 10 minutes.
________________________________________
What Happens?
• The ESP32 wakes up every 10 minutes, blinks the onboard LED, updates the LCD, and then goes back to sleep.
• It doesn’t use an external RTC module —it relies on the ESP32's internal RTC timer.
