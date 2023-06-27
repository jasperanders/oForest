# Lab Management Guide

This guide will show you how to manage your oForest lab after the initial setup. 
_This is a living document. It might not be exhaustive. Please reach out with feedback or sumbit a PR with your changes._

## Adding Researchers to your Project

Experiments are deployed by creating a new Repository in your oForest GitLab group.
Thus a researcher must be part of said group. This requires two things:

1. You, as the lab manager, must be maintainer (or owner) of the GitLab group
2. The researcher you want to add must have an GitLab account where you run oForest.

After that you can add the Researcher to the GitLab Group as a developer. 
For this go to the members section and invite them via email and select the correct role.

The new researcher now can add as many new experiments as they want.

## Allowing Access to have only one Experiment

If you don't want a researcher to create many experiments you can also create the 
experiment repository yourself and only invite them as a collaborator on this single project.
They now don't have the ability to create other experiments in your oForest group.

**But: This is only a soft security measure and does not prevent them from making changes to your cluster.** 
**Only invite people you trust to your projects.**
