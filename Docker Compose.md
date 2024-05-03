#### Grouped startups

Channel and identity
```
clear && docker-compose build vs-user-channels-db \
vs-prod-db \
vs-identity-db \
vs-identity-api \
vs-video-activity-db \
vs-video-activity-api \
vs-user-channel-api \
vs-api-gateway && \
docker-compose up vs-user-channels-db \
vs-prod-db \
vs-identity-db \
vs-identity-api \
vs-video-activity-db \
vs-video-activity-api \
vs-user-channel-api \
vs-api-gateway
```


Channel and identity
```
clear && docker-compose build \
vs-user-channels-db \
vs-prod-db \
vs-identity-db \
vs-video-activity-db \
vs-video-activity-api \
vs-user-channel-api \
vs-api-gateway && \
docker-compose up \
vs-user-channels-db \
vs-prod-db \
vs-identity-db \
vs-video-activity-db \
vs-video-activity-api \
vs-user-channel-api \
vs-api-gateway
```


Aggregation
```
clear && docker-compose build \
vs-message-broker \
vs-identity-db \
vs-identity-api \
vs-prod-db \
vs-video-api \
vs-video-activity-db \
vs-video-activity-api \
vs-social-likes-db \
vs-social-likes-api \
vs-video-comments-db \
vs-video-comments-api \
vs-social-subscriptions-db \
vs-social-subscriptions-api && \
docker-compose -p videoshare up \
vs-message-broker \
vs-identity-db \
vs-identity-api \
vs-prod-db \
vs-video-api \
vs-video-activity-db \
vs-video-activity-api \
vs-social-likes-db \
vs-social-likes-api \
vs-video-comments-db \
vs-video-comments-api \
vs-social-subscriptions-db \
vs-social-subscriptions-api
```