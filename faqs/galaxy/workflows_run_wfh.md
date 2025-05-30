---
title: Importing and Launching a WorkflowHub.eu Workflow
area: workflows
box_type: hands_on
layout: faq
contributors: [hexylena,wm75]
optional_parameters:
  wfhub_id: The numeric WorkflowHub ID
  title: The title of the workflow you want to import, can be any text
  version: Version of the workflow you want to pin
examples:
  Load a workflow by Dockstore ID: {dockstore_id: "github.com/jmchilton/galaxy-workflow-dockstore-example-1/mycoolworkflow", title: "My Cool Workflow"}
  Load a v0.1.3 of a specific IWC workflow: {dockstore_id: "github.com/iwc-workflows/kmer-profiling-hifi-VGP1/main", title: "Kmer Profiling HiFi VGP1", version: "v0.1.3"}
---

<!-- GTN:IGNORE:011 _blank is used here due to iframeing sites that (can) set x-frame-options. The contexts in which _blank is set are only visible when iframe'd -->

{% if include.wfhub_id %}
{% capture external_page %}https://workflowhub.eu/workflows/{{ include.wfhub_id }}?version={{ include.version }}{% endcapture %}

<div class="show-when-galaxy-proxy-active">

<span class="workflow" data-workflow="https://workflowhub.eu/ga4gh/trs/v2/tools/{{ include.wfhub_id }}/versions/{{ include.version }}">
  Launch <strong>{{ include.title }} (v{{ include.version }})</strong> <i class="fas fa-share-alt" aria-hidden="true"></i>
</span>
(<a target="_blank" href="{{ external_page }}">View on WorkflowHub</a>)

</div>

<div class="hide-when-galaxy-proxy-active">

<a href="https://my.galaxy.training/?path=/workflows/trs_import%3ftrs_server=workflowhub.eu%26run_form=true%26trs_id={{ include.wfhub_id }}%26trs_version={{ include.version }}">
  Launch <strong>{{ include.title }} (v{{ include.version }})</strong> <i class="fas fa-share-alt" aria-hidden="true"></i>
</a>
(<a href="{{ external_page }}">View on WorkflowHub</a>)

</div>

{% capture filter %}name:"{{ include.title }}"{% endcapture %}
{% snippet faqs/galaxy/workflows_import_search.md override_title="If this does not work" trs_server="workflowhub.eu" search_query=filter %}

{% else %}

1. Go to {% icon galaxy-workflows-activity %} [Workflows → Import](https://my.galaxy.training/?path=/workflows/import) in your Galaxy
2. Switch tabs to TRS ID
3. Ensure the *"TRS server"* is set to "workflowhub.eu"
4. Provide your your *"TRS ID"* (WorkflowHub's numerical identifier of your workflow that appears in the link to its WorkflowHub page)
5. Select the workflow version you want to import

{% endif %}
