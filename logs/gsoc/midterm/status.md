Status of jflory7's GSoC Project
================================

## What I have

### Deliverables

* https://pagure.io/jflory7-ansible/blob/master/f/playbooks/deliverables
 * https://pagure.io/jflory7-ansible/blob/master/f/playbooks/deliverables/tasks/main.yml
 * https://pagure.io/jflory7-ansible/blob/master/f/playbooks/deliverables/templates/wp-config.php
 * https://pagure.io/jflory7-ansible/blob/master/f/playbooks/deliverables/vars/all.yml

### Other learning items not specific to proposal

* https://pagure.io/jflory7-ansible/blob/master/f/playbooks/basic-provisioning/initial-centos-rhel-7-setup.yml
* https://pagure.io/ccmc-ansible/blob/master/f/playbooks

### Concerns over deliverables

* Does PHP / PHP-FPM need to be installed and configured in Fedora Infrastructure? Cannot find existing playbooks for this purpose.
* Working within the `ansible` repository for Infrastructure, and copying my changes to individual Pagure repo. Having concerns over integrating playbooks into Infrastructure (e.g. taking advantage of existing roles / tasks). Don't want to step on toes of other areas of project.
* Need to understand if there is desire to spin up WordPress sites frequently for a multi-site network (i.e. on demand) or if the desire is more for a handful of potential applications (like CommBlog and Magazine only).
* Documentation scope
 * For writing the SOP, unsure of the range of activities / information that needs to be covered
 * For installing a WordPress site only, or does it need to cover information like where the sites are hosted, how to manage them, etc.?
 * Anything else besides any "work" that needs to be done before running the playbook?

## What is planned

* "First draft" of playbook for setting up a single-site WordPress installation exists, but is not refined or properly tested as of yet
 * Next week can consist of improving / refactoring existing playbook to perform a single-site installation successfully
 * Trying to save time and effort by utilizing existing roles in `ansible` repository, e.g. mariadb-server role
 * Proving difficult to integrate the official `ansible` repository into my local testing environment, but I believe this is something that can be resolved with increased experience and testing locally

## How I need to improve

* Communication on GSoC progress hasn't been as frequent as I wanted to keep it
 * Blog posts need to happen weekly, consistently, not one-off posts
 * Aiming to be consistent with future posts
 * _Q: Is there a method of communicating progress or updates that you would prefer other than blog posts?_
* Time management problems
 * I've realized I'm overextending in other areas in the Project which is taking away time for me to focus on my project proposal
 * Need to readdress priorities and pull back from other areas to focus on GSoC proposal
* Feedback from mentor?