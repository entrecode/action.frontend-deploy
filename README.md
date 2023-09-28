# action.frontend-deploy

GitHub composite action for frontend-deploy to aws s3

## example

```yaml
deploy:
    runs-on: ubuntu-latest
    
    permissions:
      contents: read

    needs: build

    steps:
      - uses: entrecode/action.frontend-deploy@latest
        with:
          AWS_ACCESS_KEY_ID: ${{ vars.AWS_ACCESS_KEY_ID }} 
          AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          bucket_name: ${{ needs.build.outputs.bucket_name }}
```

## inputs

All inputs are requried to run the action

| Name                    | Type     | Description                                 |
|-------------------------|----------|---------------------------------------------|
| `AWS_ACCESS_KEY_ID`     | String   | AWS_ACCESS_KEY_ID as GitHub variable        |
| `AWS_SECRET_ACCESS_KEY` | String   | AWS_SECRET_ACCESS_KEY as GitHub secret      |
| `bucket_name`           | String   | Name of the s3 bucket from build.outputs    |

`AWS_ACCESS_KEY_ID` is defined in GitHub as action-variables, `AWS_SECRET_ACCESS_KEY` is defined in GitHub as action-secrets and `bucket_name` results from build-outputs. They are all required.
