# DMP Tool MUG

## Introduction

DMP Tool MUG is an innovative tool developed in collaboration with the Medical University of Graz. It leverages the principles of machine actionable data management plans (maDMPs) to streamline the creation and management of data management plans (DMPs) for medical research. Designed to seamlessly integrate with the university's existing institutional systems, the tool automates the collection of project details, research data, and personnel information. This integration minimizes repetitive data entry and enhances the accuracy and efficiency of DMP creation. DMP Tool TUGraz produces DMPs that are both human-readable, editable in formats such as Word, and machine-actionable, meeting the Science Europe’s Practical Guide to the International Alignment of Research Data Management and aligning with the RDA recommendations on maDMPs.

## Damap Project and Documentation

For an overview and instructions for running the whole damap package (backend and frontend),
refer to the [damap-backend](https://github.com/sharedRDM/damap-backend) project.

## DMPToolFrontend

This repository contains the source code for the frontend of DAMAP and need to be run
with [damap-backend]((https://github.com/sharedRDM/damap-backend)).
The project is based on [Angular](https://angular.io/) and uses [NX](https://nx.dev/) as a build system.

### Development server

Run `nx serve damap-frontend` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload
if you change any of the source files.

### Build

Run `nx build damap-frontend` to build the project. The build artifacts will be stored in the `dist/` directory. Use
the `--prod` flag for a production build.

### Running unit tests

Run `nx test damap` to execute the unit tests for the library and `nx test damap-frontend` for the application.

### Run the project with docker

For running the project in conjunction with the backend in a dockerized setup,
please refer to the [damap-backend]((https://github.com/sharedRDM/damap-backend)) project.
