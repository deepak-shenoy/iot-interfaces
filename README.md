# IOT Interfaces

## GPIO
### Overview
GPIO - General Purpose Input/Output. It is a type of pin found on the integrated circuit that
does not have a specific function. 

* Pin Mode : Each port bit of the general-purpose I/O (GPIO) ports can be individually configured by software in several modes:
  * input or output
  * analog
  * alternate function (AF).
* Pin characteristics :
  * Input : no pull-up and no pull-down or pull-up or pull-down 
  * Output : push-pull or open-drain with pull-up or pull-down capability
  * Alternate function : push-pull or open-drain with pull-up or pull-down capability.

![01-GPIO_Functional_description_graph.png](.artifacts/img/01-GPIO_Functional_description_graph.png)

https://en.wikipedia.org/wiki/General-purpose_input/output

While most pins have a dedicated purpose, such as
sending a signal to a certain component, the function of a GPIO pin is customizable and can be
controlled by the software.

## HAL (Hardware Abstraction Layer)
### Overview
The HAL (Hardware Abstraction Layer) drivers consist of a set of driver modules,
each associated to a standalone peripheral. In some cases, a module is dedicated
to a peripheral’s functional mode. 

HAL Main Features:

* Cross-Family Portable APIs: These cover common peripheral features as well as family
or device-specific peripheral features.

* API Programming Models: Most HAL drivers implement three API programming models:
polling, interrupt, and DMA.

* RTOS Compliant APIs: Fully reentrant APIs. with appropriate check and return
“BUSY” at function entry in case of the requested operation is not possible.
Systematic usage of timeouts in polling mode.

* Peripheral Multi-Instance Support: This allows concurrent API calls for
multiple instances of a given peripheral (e.g., USART1, USART2).

* User-Callback Functions: Most HAL drivers implement rely on user-callback
functions for asynchronous programming models, sush as Peripheral interrupt events
and Error events.

* Peripheral System-Level Initialization/De-Initialization: This includes clock, GPIOs,
interrupt,
and DMA, which are done at the application level using the appropriate HAL system
driver (e.g., HAL RCC, HAL GPIO, HAL Cortex, HAL DMA). These initialization sequences
are performed before configuring the given HAL driver. Note that CubeMX2 offers code
generation capabilities for these initialization sequences, and peripheral clock enabling
can be performed intrinsically during initialization if the feature is enabled in the
configuration file.

* Bus Services: AcquireBus and ReleaseBus services (for bus-type drivers like
I2C, SPI, etc.) ensure safe hardware access
to prevent concurrent access to driver processes and handle objects.

* Timeouts for Blocking Processes: Timeouts can be simple counters or time-based.
