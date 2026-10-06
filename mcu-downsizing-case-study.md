# Case study: winning over a sceptical customer on an MCU downsizing

*A written example of how I unblock delivery. Customer, product and company-specific details are anonymised.*

## Context

An automotive power-electronics ECU, an inverter for an electrified powertrain, ran on a high-end multicore microcontroller. The chip was more than the product needed. Moving to a smaller variant of the same family promised a cost reduction **in the order of millions of euros** over production volumes.

There was a catch. The smaller MCU could not carry the full load on its own, so part of the functionality had to move to a **second, small auxiliary MCU** connected over SPI.

**Status:** in validation, not yet in production.
**My role:** architecture, technical analysis, debugging and customer alignment. The code was written and integrated by colleagues in my team.

## The real problem was not technical

The customer, a major European OEM, was strongly against the change. Their concerns were reasonable:

- A second processor means a second point of failure.
- How would they flash and update the ECU? Would their production and service processes have to change?
- How would calibration work on the auxiliary MCU?
- Could the auxiliary MCU be reflashed on its own?

We had already been through several meetings. Each one ended with the same objections, and slides were not changing anyone's mind.

## What I did

**1. Kept the customer's process unchanged.**
The auxiliary MCU image is embedded inside the main firmware package. The customer still flashes **one ECU, through one process**. The same application binary also runs on both the old and the new main MCU, which makes direct correlation testing possible.

**2. Wrote the boot and flashing sequence down, step by step.**
I replaced high-level slides with a written, step-by-step description: power-up, how the main MCU brings up the auxiliary one, how the update flows across SPI, and what happens if any step fails.

**3. Was explicit about what we would *not* support.**
For example, standalone reflashing of the auxiliary MCU. It was technically feasible, but its value did not justify the additional architecture, validation and maintenance cost. Saying this clearly built more trust than promising everything.

**4. Backed every claim with measured data.**
- CPU-load measurements, with timing analysis, drove the task redesign: moving non-critical work to slower tasks, executing selected code from RAM and making security-module processing asynchronous.
- Validation was phased, first low voltage and then high voltage on the bench, and results were shared with the customer at each step.

## Outcome

The objections did not disappear overnight. They turned into **specific technical questions**, and specific questions can be answered. The customer moved from opposing the architecture to accepting it, and the project moved into validation.

Work is ongoing. At the time of writing I am investigating an intermittent SPI communication issue between the two MCUs.

## What I took from it

- A sceptical stakeholder is rarely asking for a better presentation. They are asking for **evidence** and for **honesty about trade-offs**.
- **Writing it down** turns a debate into a review. People can point at step 4 and ask a question, instead of repeating a general concern.
- **Saying no** to a feature, with a clear reason, can increase credibility.
