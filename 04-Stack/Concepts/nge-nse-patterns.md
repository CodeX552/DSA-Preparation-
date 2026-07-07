# NGE/NSE Patterns (Monotonic Stack)

## 4 Variations
| Problem | Direction | Stack Order |
|---------|-----------|-------------|
| Next Greater Right (NGR) | Right → Left | Decreasing |
| Next Greater Left (NGL) | Left → Right | Decreasing |
| Next Smaller Right (NSR) | Right → Left | Increasing |
| Next Smaller Left (NSL) | Left → Right | Increasing |

## Key Insight
Monotonic stack mein useless elements hata dete hain. Agar chhota element aaya aur hum greater dhundh rahe hain, toh chhote ko hatao — wo kisi ke kaam ka nahi.

## Applications
- **NGR**: Daily Temperatures, Stock Span
- **NSR/NSL**: Largest Rectangle in Histogram
- **All 4**: Trapping Rain Water (alternative approach)
