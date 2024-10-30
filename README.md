# DMP Tool MUG

## Introduction

The DMP Tool MUG is an innovative tool developed in collaboration with the Research Data Management team at Graz University of Technology. It leverages the principles of machine actionable data management plans (maDMPs) to streamline the creation and management of data management plans (DMPs) for medical research. Designed to seamlessly integrate with the university's existing institutional systems, the tool automates the collection of project details, research data, and personnel information. This integration minimizes repetitive data entry and enhances the accuracy and efficiency of DMP creation. DMP Tool MUG produces DMPs that are both human-readable, editable in formats such as Word, and machine-actionable, meeting the Science Europe’s Practical Guide to the International Alignment of Research Data Management and aligning with the RDA recommendations on maDMPs.

## Workflow Diagram

For a detailed view of our workflow process involving the collaboration between TU Graz and the Medical University of Graz, please refer to the diagram located in the `arch/your_file.pdf`.

## Run a demo instance
This demo instance is configured with a keycloak username `user` & password `user`.

```bash
# make sure you have docker & docker-compose installed
docker compose -f docker/docker-compose.demo.yml up
```

**visit** [http://localhost:8000](http://localhost:8000)   
