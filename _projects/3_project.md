---
layout: page
title: Cognitive radio wireless node
description: Cognitive radio ad-hoc node and network architecture for disaster management communications
img: assets/img/projects/bsc-crahn/disaster_communication.jpeg # TODO: replace with your cover image
importance: 3
category: Bachelor's Project
---

In large-scale disasters like earthquakes, conventional cellular and wired networks can fail exactly when they are needed most.  
This project proposes a cognitive radio–based **wireless** infrastructure where small nodes form a self-organizing ad-hoc network and route critical information from damaged buildings to crisis-management centers.

## Overview

- Bachelor’s project in Electrical Engineering (Telecommunications), University of Tehran.  
- Focus: design of a cognitive radio ad-hoc network (CRAHN) and its communication node for use as an emergency backbone in disaster scenarios.  
- Work includes: network architecture, routing and prioritization schemes, spectrum-agile behavior, and implementation of a representative embedded node and hardware prototype.
- Date: February 2013

<div class="row">
  <div class="col-sm-8 mx-auto mt-3 mt-md-0 text-center">
    {% include figure.liquid loading="eager" path="assets/img/projects/bsc-crahn/disaster_adhoc_comm_hierarchy.jpeg" title="System-level overview" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  System-level diagram of buildings with installed nodes forming a wireless ad-hoc network toward a central crisis-management center.
</div>

## Problem

- After events like earthquakes, tasks such as victim localization, triage, and resource allocation depend on timely and reliable situational information from the affected area.  
- Cellular and wired networks are vulnerable to physical damage, power outages, and overload, and may be unusable during the first hours after a disaster.  
- A robust, autonomous communication layer is needed that can operate independently of existing infrastructure and still provide coverage across a city through local cooperation between nodes.

## Network architecture

The project centers on a cognitive radio ad-hoc network that serves as a dedicated communication backbone for disaster management.

- Each node is deployed in buildings and participates in a multi-hop, cooperative ad-hoc network that forwards data to hardened crisis-management stations.  
- Nodes apply cognitive radio techniques: they sense the spectrum, act as secondary users, and dynamically select frequency bands depending on primary user activity and local interference.  
- Clusters of nodes share spectrum information, while gateway nodes connect clusters and relay aggregated traffic toward crisis centers.  
- City-wide coverage is realized through multiple protected stations (e.g., crisis centers) interconnected with wired or satellite backhaul.

<div class="row">
  <div class="col-sm-8 mx-auto mt-3 mt-md-0 text-center">
    {% include figure.liquid loading="eager" path="assets/img/projects/bsc-crahn/disaster_adhoc_comm.jpeg" title="Clustered CRAHN topology" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Cluster and gateway view showing multi-hop connections from building nodes to nearby crisis-management stations.
</div>

## Node behavior, priorities, and routing

Each node operates as an intelligent sensing and forwarding element in the network.

- Event detection: local sensors detect hazards (e.g., earthquake or structural impact) and trigger generation of emergency messages with context.  
- Priority model: every message receives a priority between 0 and 1, derived from factors such as local damage severity, estimated occupancy, secondary hazard risk, and strategic importance of the building.  
- Queuing: messages are stored in per-node queues where higher-priority items are transmitted earlier to reduce delay and loss under congestion.  
- Routing: ad-hoc routing (e.g., AODV) discovers and maintains multi-hop paths toward the nearest crisis-management station via on-demand route-request/route-reply exchanges.  
- Spectrum agility: when a primary user is detected or interference becomes severe on a given band, nodes switch to an alternative band while preserving connectivity.

<div class="row">
  <div class="col-sm-6 mx-auto mt-3 mt-md-0 text-center">
    {% include figure.liquid path="assets/img/projects/bsc-crahn/routing_table.jpeg" title="Priority-based queue" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
   Sketch of priority-based transmission queues.
</div>

## Hardware realization (SCH & PCB)

To validate the concepts at the physical layer, a representative embedded node was designed and implemented, including schematic and PCB.

- Processing and interfaces: an ATmega128A microcontroller provides sufficient processing power and multiple serial interfaces for interfacing with radios and sensors.  
- Radios and bands: a 2.45 GHz ISM link (Bluetooth) is used as the main short-range channel, with a 433 MHz ISM link acting as an alternative band for modeling spectrum switching.  
- Sensors and local interface: an ADXL345 3-axis accelerometer detects shocks, earthquakes, and device motion; a character LCD, LEDs, buzzer, and optional keypad support local status and interaction.  
- Schematic and PCB: a custom schematic and board integrate MCU, RF modules, accelerometer, power circuitry, and connectors in a compact design suitable for installation in buildings.

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/projects/bsc-crahn/disaster_adhoc_node_SCH_PCB.jpeg" title="Prototype node hardware" class="img-fluid rounded z-depth-1" %}
 
  </div>
</div>
<div class="caption">
  Prototype node: the schematic/PCB layout used to realize the communication node.
</div>
