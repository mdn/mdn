## Architectural Decision Records for MDN Documentation and Software

This directory holds ADRs ([Architectural Decision
Records](http://thinkrelevance.com/blog/2011/11/15/documenting-architecture-decisions))
that document important decisions we have made about our documentation
and our software.

### How to Propose an ADR

- Figure out what number your ADR will be. Look at the ADRs that are
  already in this directory, and check the pull requests on this repo
  for pending ADRs, then pick the next highest number.

- Create a new file with the name of the form
  `NNN-short-description.md`. You can do this without using git by
  just clicking the "Create new file" button in Github.

- Copy the contents of the file `000-TEMPLATE.md` into your new
  file. If you working directly on GitHub, open this link in a new tab
  and copy-and-paste the template text:
  https://raw.githubusercontent.com/mdn/mdn/master/ADRs/000-TEMPLATE.md

- Fill out the template with the details of your proposed decision.

- Submit a pull request for your new ADR file, and participate in any
  discussion in the PR while your proposed ADR is being
  considered. Your ADR can be refined while in PR form, so don't feel
  that you must have it in final form before submitting the PR.

### How ADR Proposals are Adopted or Rejected

- We will use the DACI decision making framework for our ADRs, and the
  ADR template will require you to specify the Driver, Approver,
  Consultants and the Informed for your ADR.

- If you are the one creating the ADR document, you are likely also
  the Driver for the decision. You're the one doing the research and
  pushing for a decision to be made.

- Each ADR should specify who the Approver for the decision will
  be. Typically this is a single person with appropriate expertise and
  authority to make the decision. The Approver is the person who will
  update the ADR status from "Proposed" to "Approved" or "Rejected"
  and merge the pull request.

- The C in DACI stands for consultants (or collaborators or
  co-authors). This should be a small group people who have worked
  with you on your proposal or who have participated in the discussion
  leading up to the ADR. These are also people who may be interested
  in commenting on the pull request.

- The I in DACI represents the people who do not need to participate
  in making the decision but who do need to be informed of the
  decision once it is made.
