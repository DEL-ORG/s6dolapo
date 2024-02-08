# Use an official PostgreSQL image as a base
FROM postgres:latest

# Install necessary tools
RUN apt-get update && \
    apt-get install -y \
        python3 \
        python3-pip \
        curl \
        unzip \
        groff \
        less \
        && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && \
    unzip awscliv2.zip && \
    ./aws/install && \
    rm -rf aws awscliv2.zip

# Set environment variables for AWS CLI
#ENV AWS_ACCESS_KEY_ID='AKIAZI2LE2Z6CLDSGQZ7'
#ENV AWS_SECRET_ACCESS_KEY="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"
#ENV AWS_DEFAULT_REGION='us-east-1'
#ENV DB_NAME='s6-user'
#ENV DB_USER='doadmin'
#ENV DB_HOST='db-postgresql-nyc3-26515-do-user-12198957-0.c.db.ondigitalocean.com'
#ENV DB_PORT='25060'
#ENV DB_PASSWORD='AVNS_HkmaatXJL1QfH60HmnZ'
#ENV S3_BUCKET='del-db-backup/S6/s6dolapo/'
# Set the working directory
WORKDIR /backup

# Copy backup script into the container
COPY . .

# Grant execute permissions to the script
RUN chmod +x /backup/backup.sh

# Run the backup script as the entrypoint
CMD ["./backup.sh"]
