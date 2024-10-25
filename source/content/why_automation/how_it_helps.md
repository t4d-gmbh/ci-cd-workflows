### How automation helps
{% if build == "slides" %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./benefit_healthy_ref
./benefit_collab
./benefit_quality
./benefit_transparency
./benefit_reproducibility
```
{% else %}
<!-- imported in parent index -->
{% endif %}

{% if page %}
## Conclusion

In summary, automation in GitLab and GitHub significantly contributes to maintaining a healthy reference, fostering collaboration, increasing quality, ensuring transparency, and enhancing reproducibility. By leveraging these automation features, teams can streamline their workflows and improve overall project outcomes.
{% endif %}
