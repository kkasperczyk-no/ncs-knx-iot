.. _release_notes_v070:

Release notes for |addon| v0.7.0
################################

The |addon| v0.7.0 release for the |NCS| integrates the KNX IoT Point API stack v1.1.0.

This is an `experimental <Software maturity levels_>`_ release.
Use it for evaluation and testing only, and not in production.

.. contents::
   :local:
   :depth: 2

This |addon| release is compatible with |NCS| v\ |ncs_version|.

For the list of current issues, see :ref:`knx_iot_known_issues`.

Changelog
*********

Added:

   * Support for ETS commissioning and OpenThread Joiner as the default configuration of the :ref:`knx_iot_samples`.
     The development configurations, hardcoded KNX commissioning, hardcoded Thread commissioning, and manual Thread bring-up through the shell are now optional overlays.
   * The :option:`CONFIG_KNX_SERIAL_NUMBER` Kconfig option for setting the KNX serial number.
   * Support for the nRF54LC10 DK in the :ref:`knx_iot_samples`.
   * Support for the nRF54L15 TAG in the :ref:`knx_iot_light_switch_sensor_sample` sample, with the single button and RGB LED user interface layout (:option:`CONFIG_KNX_UI_LAYOUT_SINGLE_BUTTON_RGB`).
   * Datapoint persistence.
     The :ref:`knx_iot_light_switch_actuator_sample` sample now stores its light state and restores it after a reboot.
   * Read-on-init tracking for group objects with the Read on Init (I) flag. 
     You can configure it with the :kconfig:option:`CONFIG_KNX_READ_ON_INIT_RESPONSE_TIMEOUT_MS` and :kconfig:option:`CONFIG_KNX_READ_ON_INIT_RETRIES` Kconfig options.
   * The flash LED mode, which produces a short flash once per second.
   * Support for signed 32-bit (``value4Count``) datapoints.
   * The :ref:`knx_iot_certification_sample` sample for verifying KNX IoT compliance with the |EITT| certification tests.

* Updated:

   * KNX IoT Point API Stack to version 1.1.0.
     For information about adapting applications, see the :ref:`KNX IoT migration guide <knx_iot_migration>`.
   * The |NCS| version to v3.4.1.
   * Replaced the :file:`samples/common/verbose_logging.conf` Kconfig fragment with the ``knx-verbose-logging`` snippet.
     The snippet also increases the console UART baud rate to 1000000.
   * Hardcoded commissioning now configures a complete group object table.  
     As a result, the samples can use both switching channels with hardcoded commissioning.
   * Devices with hardcoded commissioning now derive their serial number and individual address from the hardware device ID by default (:option:`CONFIG_KNX_HARDCODED_IDENTITY_HWINFO`).
     This allows you to flash the same image to several devices with the same role.
   * The board user interface is now defined by a layout table that you select with the ``CONFIG_KNX_UI_LAYOUT`` Kconfig choice.
   * The :ref:`knx_iot_light_switch_sensor_sample` sample now toggles based on the light state reported by the actuator.
   * The |addon| now enables the :kconfig:option:`CONFIG_OPENTHREAD_MLR` Kconfig option by default.
     This allows a Thread Border Router to forward KNX IoT site-local multicast messages from the infrastructure link to the device.

Fixed:

   * An issue where the light state of the :ref:`knx_iot_light_switch_actuator_sample` sample was not persisted after a reboot (:ref:`KRKNWK-22216 <knx_iot_known_issue_actuator_state_not_persisted>`).
