# Docker meta action

This action outputs some Docker metadata, like tags and labels.

## Inputs

### `default-branch`

The name of the default Git branch.
This will be filled in automatically if not provided.

### `images`

**Required** Docker images separated using commas.

### `strip-tag-prefix`

The prefix to strip from the tag.
For example, for `prefix/v1.2.3` you can use `prefix/`.

### `include-pipeline-id`

Include a tag that contains the branch name and the pipeline ID if set to `true`.

## Outputs

### `tags`

A list of tags separated using commas.

### `labels`

A list of labels separated using commas.

## Example usage

```yaml
- name: Docker meta
  uses: zazuko/action-docker-meta@main
  id: docker_meta
  with:
    images: ghcr.io/org/image

- name: Build and push Docker images
  uses: docker/build-push-action@v2.1.0
  with:
    # ...
    tags: ${{ steps.docker_meta.outputs.tags }}
    labels: ${{ steps.docker_meta.outputs.labels }}
```
