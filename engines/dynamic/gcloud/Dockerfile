FROM  quantumgears/ai-dev:flask-base-v1

ENV BASE_DIR  "/ai-prod/quanta"
WORKDIR $BASE_DIR

COPY ai  ./ai
COPY pdfengine ./pdfengine
COPY nlp ./nlp
COPY common_api ./common_api
COPY train ./train
COPY swagger ./swagger
COPY splunk_api ./splunk_api
COPY quanta-data ./quanta-data
COPY gcloud ./gcloud
RUN pip install --upgrade google-cloud-storage
ADD quanta_main.py quanta_load.py quanta_global.py Riz_GCloud_Auth.json ./

EXPOSE 8080

#ENV 'QUANTA_DOCKER_SPIN_DYNAMIC_FRM_DJANGO' 1
ENV QUANTA_PDF_PROCESSING_MODE 'singlethread_newprocess'
ENV QUANTA_PDF_PAGES_PER_CHUNK 5
ENV QUANTA_GCLOUD_SUB 'rizsub'
ENV QUANTA_GCLOUD_PROJID 'ml-dev-0001'
ENV OMP_THREAD_LIMIT 1
ENV QUANTA_GCLOUD_SERVICES 'True'
ENV GOOGLE_APPLICATION_CREDENTIALS '/ai-prod/quanta/Riz_GCloud_Auth.json'
ENV NLTK_DATA $BASE_DIR/nlp/nltk_data
CMD python quanta_main.py
