# Docker meta action

This action outputs some Docker metadata, like tags and labels.

## Inputs

### `default-branch`

The name of the default Git branch.
This will be filled in automatically if not provided.

### `image`

**Required** Docker image.

## Outputs

### `tags`

A list of tags separated using commas.

## Example usage

```yaml
- name: Docker meta
  uses: zazuko/action-docker-meta@main
  id: docker_meta
  with:
    image: ghcr.io/org/image

- name: Build and push Docker images
  uses: docker/build-push-action@v2.1.0
  with:
    # ...
    tags: ${{ steps.docker_meta.outputs.tags }}
```
