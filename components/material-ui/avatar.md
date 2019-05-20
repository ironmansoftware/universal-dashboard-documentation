# Avatar

## Image Avatar

```text
New-UDMuAvatar -Image 'https://avatars2.githubusercontent.com/u/34351424?s=460&v=4' -Alt 'alon gvili avatar'
```

![Image avatar](../../.gitbook/assets/image%20%2835%29.png)

## Image Avatar with Custom Style

```text
New-UDMuAvatar -Image 'https://avatars2.githubusercontent.com/u/34351424?s=460&v=4' -Alt 'alon gvili avatar'  -Style @{width = 80; height = 80}
```

![Image Avatar with Custom Style](../../.gitbook/assets/image%20%287%29.png)

## Square Image Avatar

```text
 $AvatarProps = @{
  Image = 'https://avatars2.githubusercontent.com/u/34351424?s=460&v=4'
  Alt = 'alon gvili avatar'
  Id = 'test-avatar'
  Style = @{width = 150; height = 150; borderRadius = '4px'}
}
New-UDMuAvatar @AvatarProps
```

![Square Avatar](../../.gitbook/assets/image%20%2823%29.png)

