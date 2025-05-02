# Memory as Error Correction – Sage Simulation

This SageMath simulation models how different error-correcting codes perform under varying levels of random noise. The goal is to draw parallels between mathematical error correction and different types of human memory, such as short-term, episodic, and semantic memory.

## Project Overview

The simulation sends messages through a Binary Symmetric Channel (BSC), where each bit has a fixed probability of being flipped. Three types of codes are used to encode and decode the messages:

- **Repetition Code [7,1]** – Simplest form of redundancy; majority vote decoding
- **Hamming Code [7,4]** – Classical error-correcting code; corrects single-bit errors using syndrome decoding
- **Locally Recoverable Code [7,4]** – Custom code with local and global parity bits; allows recovery from localized errors

The success rate of decoding is measured for each code across a range of flip probabilities from 0.01 to 0.30.

## File Contents

- `my_binary_symmetric_channel(v, p)` – Simulates bit flips in a codeword based on flip probability `p`
- `repetition_encode(bit)` and `repetition_decode(codeword)` – Encode/decode functions for the repetition code
- `my_Hamming_code(r)` – Returns the generator matrix for a Hamming code with redundancy `r`
- `hamming_decode(H, received)` – Syndrome decoding function for Hamming code
- `lrc_encode(message)` and `lrc_decode(received)` – Custom implementation for a [7,4] Locally Recoverable Code
- `simulate_trials_for_[code](...)` – Run multiple trials for each code type and return decoding success rates
- `plot_success_rates(...)` – Generates a line plot comparing decoding success for all three codes

## How to Run

1. Open the SageMath environment or Jupyter Notebook
2. Define all functions in the script
3. Run simulations:
   ```python
   p_list = [0.01 * i for i in range(1, 31)]
   repetition_success = simulate_trials_for_repetition(p_list, 1000)
   hamming_success = simulate_trials_for_hamming(G, H, p_list, 1000)
   lrc_success = simulate_trials_for_lrc(p_list, 1000)
