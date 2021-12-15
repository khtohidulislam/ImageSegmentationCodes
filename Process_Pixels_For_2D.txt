imdsimagesTr = 'E:\3D CNN\preprocessedDataset2D\Backup\imagesTr';
imdslabelsTr = imageDatastore('E:\3D CNN\preprocessedDataset2D\Backup\labelsTr',...
    'IncludeSubfolders',true,...
    'LabelSource','foldernames');

saveDirimagesTr = 'E:\3D CNN\preprocessedDataset2D\Tumor and Non Tumor\imagesTr';
saveDirlabelsTr = 'E:\3D CNN\preprocessedDataset2D\Tumor and Non Tumor\labelsTr';

% Define Number of Files/Images
nFiles = numel(imdslabelsTr.Files);

for fIdx = 1:nFiles
    ImageslabelsTr = imread(imdslabelsTr.Files{fIdx});
    pixelCount=sum(ImageslabelsTr(:));
    if pixelCount>=120
        % Extract filename for the title
        [~,fileNamelabelsTr,fileExtlabelsTr]=fileparts(imdslabelsTr.Files{fIdx});
        fullFileNamelabelsTr = fullfile(saveDirlabelsTr, [fileNamelabelsTr, fileExtlabelsTr]);


        ImagesimagesTr = imread(fullfile(imdsimagesTr, [fileNamelabelsTr, fileExtlabelsTr]));
        fullFileNameimagesTr = fullfile(saveDirimagesTr, [fileNamelabelsTr, fileExtlabelsTr]);

        imwrite(ImageslabelsTr, fullFileNamelabelsTr);
        imwrite(ImagesimagesTr, fullFileNameimagesTr);

    else

    end

end